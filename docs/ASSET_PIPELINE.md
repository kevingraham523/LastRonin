# Asset pipeline

Version 1.0 • 12 October 2026. Preserve original inputs and accepted derivatives. See [TECH_SPEC](TECH_SPEC.md) for actual locations, [INTEGRATION_CONTRACTS](INTEGRATION_CONTRACTS.md) for exact fields, and [QA_CHECKLIST](QA_CHECKLIST.md) for promotion gates.

## Intake and provenance

1. Assign actor/ENV/module ID, story era, owner and board task. Check selected reference against the art bible. Standard Synja is blue-gray; elite Synja is white/red; Foot Bot has purple accents. A generic filename does not establish character identity.
2. Record source filename/provider, generation or download date if known, tool version/settings if known, source/reference hashes and rights/source notes. Unknown provenance stays unknown. Do not infer licensing from file availability or publish raw purchased/downloaded packs as a side effect of intake.
3. Preserve source bytes. Copy into the owning role's `source/` area only in a scoped intake change; put editable derivatives in `work/`, export candidates in `exports/`, and evidence in `qa/`. Keep old accepted versions and record replacement links. The current setup records external files without moving or duplicating the working library into Git.
4. Integration selects regular Git versus Git LFS or a documented artifact store before broad binary intake. Any store must support a fresh clone with explicit retrieval/version/hash instructions. No silent history migration. Generated caches and editor backups are not authoritative assets.

Suggested paths, once intake is assigned:

```text
assets/characters/ronin/{source,work,exports,qa}/
assets/characters/<actor_id>/{source,work,exports,qa}/
assets/environments/<kit_id>/{source,work,exports,qa}/
tools/blender/animation/
tools/blender/environment/
docs/workstreams/<role>/<task>/HANDOFF.md
```

## 3DAIStudio to Blender

Use the user's selected turnaround or model as the reference; this task does not generate replacement characters. Keep base-character weapons/extras separately identifiable. Record the exact 3DAIStudio export and textures; do not assume a screenshot is a mesh, that a rig exists, or that every generated character is humanoid.

Open a copy in Blender. Audit real dimensions, orientation, geometry, nonmanifold/loose pieces, normals, UVs, material slots, missing textures, mesh intersections and joint topology. Inspect shell, cloak, shoulder/armpit, hips, knees, hands and feet at game-camera size. Any remesh/decimation/material bake is a new derivative with silhouette, UV and deformation comparison; never destructively simplify the delivered rig.

Normalize units/origin on the working derivative before new rigging, retaining a source-to-working transform record. Do not apply transforms to an already rigged library blindly. Freeze a versioned rest pose, bone hierarchy, deformation map and scale after approval. Mechanical/flying/nonhumanoid assets require their own articulated rig; do not force them into a humanoid auto-rigger.

The current Ronin source is available, not a missing rig to rebuild: `RONIN_RIG`, 37 bones, IK legs with pole controls, FK upper body and skeletal cloak/tabard. The body has 22,449 vertices and 17,801 polygons; polygon count is not necessarily triangle count. A packed 2048² color texture exists. There is no facial or finger rig and no physical cloth collision system. Preserve the existing hand shape unless an assigned weapon-grip task changes it.

## Mixamo and authored animation

Keep each original motion with source name, native rate/range, download settings if known and hash. Distinguish a Mixamo source skeleton from the Ronin target. The source motion does not prove compatibility with a shell, broad shoulders, short proportions or cloak.

Retarget on a copy using explicit bone mapping and reference poses. Solve hips/root scale, shoulder/clavicle orientation, elbow clearance, knee pole direction, ankle/sole contact and cloak response. Bake evaluated motion to a candidate while keeping original source and working controls. Record in-place versus translating/turning motion independently. Preserve earlier clips unless changing them is the explicit task.

Existing approved authoring deliveries include corrected Sad Walk, narrowed-arm Mutant Run, Breathing Idle, Left 45 / Right 45 / Right 90 turns, Punch, Jump and Weighted Ninja Walk. Current library has 11 Ronin actions plus a diagnostic; the manifest also preserves original timing variants and an explicit excluded-source row. **Do not add Mutant Walking.** Existing animations establish asset availability, not final runtime combat/traversal scope.

Use 30 fps as the current library's authoring timebase; retain the standalone 24 fps weighted walk unchanged. Do not globally set an old file to 30 fps without rescaling keys and proving timing equivalence. Export loops include the interpolation closing key, with half-open playback/events as specified in the contracts. Turn clips preserve their resulting heading. Preview at normal speed and slow speed, from side/front and fixed gameplay camera. Pay special attention to the previously reported upward hitch near the end of foot recovery and wide run elbows.

Historical QA sampled 2,472 poses across eight actions plus 210 Sad Walk samples. It found no sampled sole penetration, sub-.09 mm maximum IK error and matching seams/loop endpoints, but local shoulder deformation reached approximately 5.5× edge stretch in punch/jump. Those are historical measurements, not proof that arbitrary blends or engine exports pass. Fresh metadata comparison in this setup confirms action records, not a new full pose QA run.

## Blender to game export

Use a versioned GLB/glTF 2.0 export candidate and explicit settings; do not make `.blend` auto-import a hidden build dependency. Export only accepted character mesh, skeleton, textures/materials and selected animations. Keep source rigs, staging cameras/lights, diagnostic action and source-motion collections out. Produce a full character candidate first; animation-only libraries follow only after exact skeleton compatibility is proved.

Bake constraints/IK on a duplicate export skeleton, retaining root translation/yaw through an explicit structural root. Record source action → exported animation names, ranges, sample rate and rig fingerprint. Do not strip a nondeform root and lose its motion. Verify normals/tangents, alpha, packed textures, material appearance, scale and all referenced files. Do not promise Blender preserve-volume skinning, procedural materials or six-influence weights will reproduce unchanged in the target runtime. Evaluate the actual import and document any approved derivative weight/material conversion.

Round-trip the candidate into a fresh scene and then the pinned Godot version. Compare rest pose and representative extreme/loop/contact poses against the source. Check root travel/yaw, duration, sockets, seams, shell/cloak intersections, hand grip and loop closure. Test state transitions separately. A candidate becomes `engine_validated` only with those results; currently none of the animation manifest rows are engine-ready.

Integration stages accepted character exports under `godot/characters/<actor>/`. Gameplay supplies the motor wrapper and state adapter, using semantic clip/socket IDs. Imported scenes stay replaceable. A model swap must not alter map collision, mission flags, camera decisions or attack timing without an explicit contract change. Official Godot [import configuration](https://docs.godotengine.org/en/stable/tutorials/assets_pipeline/importing_3d_scenes/import_configuration.html) supports imported animation configuration; use version-matched settings after D05 is resolved.

## Modular 2D art and environment assembly

Start with an approved camera/profile and map module brief. 3DAIStudio or Blender geometry may provide reference, projection or hidden collision; the locked visible environment direction remains illustrated modular 2D. Do not replace it with final visible procedural 3D because the prototype uses boxes.

Keep editable layered art, export PNG RGBA candidates and machine-readable spatial metadata. Separate ground, facade/corner, roof/stairs, foreground occluders, props, gate/panel states, signage, skyline and weather. Assign stable ENV family plus piece IDs. Record camera, pixel/world scale, pivot, image dimensions, anchor/elevation, footprint, seam adjacency, occlusion behavior and interaction state. Crop changes must update pivot metadata. Do not invent a pixels/metre value before the hybrid spike; block final production exports until D02 is resolved.

Export a small representative kit before bulk generation: street/facade corner, both stair connections/roof, foreground occluder and gate/panel. Assemble with the actual Ronin under the same camera. Validate ground contact, 4.8 m roof placement, depth order, facade cutaway, alpha fringes, texture seams, apparent light direction and small-screen readability. Baked shadow, runtime shadow and character contact shadow must not double-darken the same area. Art cannot narrow the alley or obstruct stairs by changing metadata silently.

BLOCK01 ENV001–044 are procedural reference families; there are no verified final modular 2D exports. ENV045–052 are later-story kit packages requiring approved maps and module breakdowns, not eight ready-made levels. ENV052 is conditional prologue scope. Keep background tower/skyline nonplayable. Interiors, climbable fire escapes and new routes require approved map changes.

Environment owns assembly scenes under `godot/environments/` and supplies collision/navigation/height metadata. Gameplay instantiates the accepted scene and connects gates/interactions through stable IDs. Environment does not edit main scene, input map or player controller. Browser import uses the same spatial contract through its adapter; selecting a renderer/loader is still a spike, not a completed conversion.

## Release and handoff

Each candidate handoff includes exact source/export hashes, asset/rig/camera/contract versions, all dependencies, reproduction command, manifest proposal and QA report. Include first-frame/loop/transition previews at the gameplay camera and list unresolved limits. Do not mark a kit or clip complete merely because a file exists. Integration validates in a clean worktree, stages accepted runtime files, updates both manifests and records rollback/replacement IDs. Originals remain preserved.
