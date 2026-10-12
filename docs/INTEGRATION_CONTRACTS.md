# Integration contracts

Contract version **1** • 12 October 2026. These are the rules for new deliveries. Existing sources remain unchanged and may not yet conform. Drafts can contain unresolved fields; an integration-ready package cannot. Technology/tuning choices explicitly marked pending stay pending.

## 1. Identity, files and promotion

Use existing `CHR01`–`CHR18`, `EN01`–`EN09`, `LOC01`–`LOC31`, `MIS01`–`MIS18`, `ENV001`–`ENV052` and `ANM001`–`ANM060` identities from the bibles. Never reuse a retired ID for another subject. FAMILY/FALL/LOST/RETURN/FINAL are story scopes, not shipping chapter indices. BLOCK01 is a map/milestone; MIS18/LOC25/ENV052 remain conditional proposals. LOC26–31 and LEG01–04 are legacy-only.

Every delivery includes `contract_version: 1`, stable ID, `asset_version` (semantic version string), owner, relative source/export paths, SHA-256 of delivered files, tool versions, provenance, applicable actor/era/map, dependencies and QA report. Paths are UTF-8, case-sensitive and forward-slash relative to repository root; runtime engine paths are relative to `godot/`. No external absolute path is a runtime dependency. The manifests' external source aliases are inventory evidence only.

Promotion sequence: `source_only` → `authoring_available` → `export_candidate` → `engine_validated` → `accepted`. Planned requirements start `planned_blocked` or `conditional`; diagnostics stay `diagnostic_only`; rejected user scope stays `excluded_by_user`. An external asset is `authoring_external`, never implicitly delivered to Git. Only integration promotes after consumer QA. A source reference or screenshot cannot satisfy an export requirement. Missing model: development gets a visibly labeled placeholder and an error report; release validation fails. Missing attack/mission/collision data: reject the package; never silently substitute a random clip or skip an objective.

Shared manifest changes belong to integration. Producers propose rows in their task handoff. A breaking ID, skeleton, timebase, path or event change increments contract major version and supplies consumer migration and rollback notes. Additive optional fields increment document minor version; unknown required schema versions fail with a clear diagnostic.

## 2. Space, scale, camera and time

| Property | Contract |
| --- | --- |
| Runtime space | Right-handed; 1 unit = 1 metre; +Y up, +X east/right on map, -Z toward north/tower. Actor local forward = -Z. Map data stays in B1 world coordinates. |
| Runtime actor origin | Ground contact centre at feet. Collision and visual are separate children of motor root. Scene root scale `[1,1,1]`; apparent height is metadata, not controller scale. |
| Existing Blender source | Z up, forward -Y, anatomical left +X. Keep authoring source intact. Engine orientation is corrected in a derived export/wrapper only. |
| Conversion invariant | A normalized source vector `(x,y,z)` must reach actor-local runtime `(-x,z,y)`; source forward maps to -Z, up to +Y. Exporter axis conversion plus wrapper rotation must combine to that mapping **once**, never twice. Validate with forward/up markers and a root-motion test. |
| Rotation | Store right-handed yaw in radians around +Y; positive yaw rotates -Z toward -X. Existing action yaw degrees remain raw authoring metadata; adapter converts once. |
| Simulation | New gameplay contract uses fixed 60 Hz simulation; rendering can vary. Existing B1 substep loop remains baseline until migration QA. Game time freezes during pause; render time cannot deal damage. |
| Animation time | Seconds from clip start, positive playback rate. Frames only in authoring inventory. No implicit 24/30/60 fps conversion. |
| Art camera | Orthographic with fixed orientation. `camera_profile_id`, yaw, pitch, vertical span, aspect/framing rules and follow limits required. B1 35°/46°/24 m is a **spike reference**, not a final asset export approval. |

The existing HTML actor faces local +Z at zero angle. Its adapter must translate heading to the -Z actor convention (yaw = existing angle + π, normalized); do not rotate the entire map. Source 3D exports must be measured after import rather than relying on a format name to prove axis correctness.

Final art export requires D02 numeric camera/pixel scale. A camera profile change invalidates dependent 2D projections and triggers environment revalidation; animation bone data is not rebuilt for a camera change.

## 3. Character and animation boundary

Runtime wrapper hierarchy (planned): `ActorRoot` owns motor/collision/game state; `VisualRoot` owns orientation/scale adapter; imported skeleton/mesh are below it; animation adapter consumes semantic state; sockets expose attachments. Gameplay uses actor/clip/socket IDs, never hardcoded Blender object paths. Imported source scenes contain no mission, damage or input scripts.

Current authoring facts: `RONIN_RIG`, `Ronin_Body`, 37 bones / 32 deform bones, 22,449 vertices / 17,801 polygons, packed 2048² color image. Structural controls are `CTRL_root`, `CTRL_foot_IK.L/R`, `CTRL_knee_pole.L/R`. Deform chains include `hips`, `spine`, `chest`, `neck`, `head`; `clavicle`, `upper_arm`, `forearm`, `hand`, `thigh`, `shin`, `foot`, `toe` with `.L/.R`; nine cloak and two tabard bones. Preserve names/rest pose in the source. There are no articulated finger or facial controls. Export rig mapping is not yet accepted.

Bake evaluated IK and cloth-bone transforms onto a derived export skeleton. Retain a structural motion root in that derivative even if control-only bones are removed. Removing nondeform `CTRL_root` without preserving its motion loses translation/turns. Do not export source Mixamo rigs, lights, cameras, QA meshes or hidden reference collections. Six skin influences in the shoulder/cloth region and Blender preserve-volume deformation need a measured import comparison; no automatic weight pruning or claim of equivalent engine skinning.

Each runtime clip descriptor must carry:

| Field | Required meaning |
| --- | --- |
| `clip_id`, `actor_id`, `rig_id`, `rig_version` | Immutable clip alias and compatible skeleton identity; bind/rest hierarchy fingerprint included in rig handoff. CHR01 identity/era must be confirmed before acceptance. |
| `source_action`, `export_animation`, `export_path` | Exact source action plus exact imported animation key; these may differ via explicit mapping, never by guessing. |
| `duration_s`, `loop`, `sample_fps` | Positive duration, boolean loop, source sampling rate; all event times within duration. |
| `motion_policy` | `in_place`, `translation`, `rotation` or `translation_rotation`. Diagnostic clips are not runtime candidates. |
| `root_track`, `root_delta_m`, `root_yaw_rad` | Explicit exported motion source; zero for in-place horizontal travel. Vertical jump intent requires D11. |
| `events`, `transitions`, `cancel_windows` | Ordered events and explicit allowed destinations, blend duration and interrupt rules; unresolved combat timing blocks combat acceptance. |
| `sockets` | Semantic socket mapping and local transforms in metres/radians; required weapon attachments cannot be guessed from mesh shape. |

Proposed semantic sockets: `weapon_primary` → `hand.R`, `weapon_secondary` → `hand.L`; these are **candidate anchors**, with transforms/weapon grip to be authored and reviewed. Existing hands do not automatically close around a weapon. Additional back/holster sockets require explicit transforms; no weapons are considered equipped merely because a reference drawing carries them.

Loop samples use half-open playback interval `[0,duration_s)`. For a source looping range 1…N with closing key N+1, duration = N/fps; keep the closing key as interpolation endpoint and do not duplicate its event/sample on wrap. One-shot duration = `(last_key-first_key)/fps`. For example run: 44/30 s, closing key 45; Sad Walk: 52/30 s, closing 53; idle: 120/30 s, closing 121. Weighted walk: 40/30 s in current library, 32/24 s in original. Turn Left 45 duration is 40/30 s, not 41/30 s. Do not reset a turn's accumulated heading at the next transition.

**Motion authority:** default integration spike uses motor-driven in-place locomotion; final adoption remains D07. When root motion is selected, animation adapter proposes a delta, motor sweeps it against collision, and the resulting actor displacement becomes authoritative. Never add root displacement and velocity movement twice. Visual root follows accepted displacement. Blocked movement cannot push through walls. Root turn motion is either consumed once by motor or removed in a derivative in-place turn—not silently canceled. Root-loop displacement accumulates across wraps.

Do not silently retime locomotion to match B1 tuning. The authored run translates approximately 2.993 m in 44/30 s (~2.04 m/s); B1 default running is 7.425 m/s. This mismatch requires explicit stride/playback/tuning review. Speed changes and blends need foot-contact QA. Keep the heavy but agile turtle feel, corrected late-step recovery and narrowed elbows.

`ANMxxx` rows are design requirements/packages; `ronin_*` rows are observed source assets. Linking them records candidates, not automatic fulfillment. Existing Punch is not an approved weapon attack; existing Jump does not enable jumping; QA range is never shipped; Mutant Walking remains excluded.

## 4. Animation events and combat authority

Only gameplay applies damage and state changes. Animation/audio/VFX listeners cannot independently award damage, healing, mission completion or gate unlocks.

Event envelope: `{contract_version, instance_id, action_instance_id, event_id, event_type, clip_id, cycle_index, time_s, payload}`. IDs are strings; instance/action IDs are unique per spawn/action; `cycle_index` is a nonnegative integer; `time_s` is finite clip-local seconds. Events are ordered by time then event_id. Runtime deduplicates `(instance_id, action_instance_id, cycle_index, event_id)`. Crossing several event times in one tick dispatches all in order; pausing dispatches none. Starting a clip dispatches its time-zero events once. Loop wrap dispatches the previous tail then the new cycle's time-zero events once. Seeking for preview emits no gameplay events; loading reconstructs state rather than replaying damage.

Allowed event types and owners:

| Event | Consumer and rule |
| --- | --- |
| `attack_window_open` / `attack_window_close` | Combat opens/closes an approved attack_id hit volume. Cancellation, defeat or missing close forces closure. |
| `foot_contact` | Surface-aware presentation cue only; `foot` is L/R. No movement or damage authority. |
| `interaction_commit` | Interaction system validates pending target, range, floor and prerequisites again; consumes once. Clips without this event use explicitly configured immediate commit. |
| `action_complete` | State machine transitions through approved graph; one-shot emits once. |
| `cue` | Audio/VFX references approved cue_id; missing optional cue logs and continues, required warning cue blocks release QA. |

Attack descriptor: `attack_id`, weapon_id, clip_id, startup/active/recovery seconds, local hit shape and height interval, allowed facing/turn rate, target factions, damage/resource data, obstruction policy, per-target hit limit, cancel windows and response IDs. D07 supplies values. Default hit limit is **one per target per action instance**; explicit approved multi-hit attacks must declare separate window IDs/limits. Rendering overlap alone is not a hit: verify spatial hit, compatible floor/height and wall obstruction. Visual root and hit-volume origin share the motor pose. Do not infer active frames from a punch's maximum extension.

## 5. Environment, 2D art and map boundary

Environment package supplies visible art and explicit spatial metadata. Gameplay consumes colliders, walkable surfaces, links, interactions and spawns; it never infers them from transparent pixels. Environment agents cannot change routes by silently changing art pivots.

Required module descriptor fields:

| Field | Type and rule |
| --- | --- |
| `environment_id`, `module_id`, `asset_version` | ENV family plus stable piece ID (e.g. `env018_stair_a`); a family package is not a finished module. |
| `camera_profile_id`, `pixels_per_metre` | Agreed profile and positive scale; unresolved values block final exports. |
| `image_path`, `image_size_px`, `pivot_px` | Relative lossless RGBA image and dimensions; pixel origin upper-left, pivot measured from that origin. |
| `anchor_m`, `bounds_m`, `height_band_m` | Local runtime-space foot/attachment anchor, 3D extent, `[min_y,max_y]` with min ≤ max. |
| `layer` | `ground`, `structure`, `foreground`, `prop`, `background` or `effect`; not a collision class. |
| `occlusion_mode` | `none`, `depth`, `cutaway` or `foreground_mask`; each mask/state path and activation rule explicit. |
| `colliders`, `surfaces`, `links` | Stable IDs and spatial data below; decorative items provide empty arrays explicitly. |
| `states`, `interaction_anchors`, `seams` | State-to-art/collision mapping, usable anchors and compatible attachment edges. |

Raster source/export convention for the first spike: lossless PNG RGBA, straight alpha, sRGB color; keep layered originals separately. Engine import may convert internally but must not produce fringes. Final pixels/metre, texture budgets, atlas policy, alpha/depth/shader implementation and shadow method are D02/D09 gates. Do not bake gameplay HUD or permanent contact shadows into foreground art. Never allow unrestricted camera-facing billboard rotation to expose an unsupported angle.

Map descriptor requires `map_id`, scope label, LOC IDs, MIS IDs, `camera_profile_id`, world bounds, module instances/transforms, actor spawn descriptors, connections, interactions, encounters and checkpoint IDs. Each spawn has stable `spawn_id`, actor_id, era, position, yaw and surface_id. Each exit specifies destination map/spawn and prerequisites; no destination may be an unresolved string in a release map.

Collider: stable ID, footprint polygon in X/Z (counterclockwise when viewed from +Y), finite vertices, bottom/top Y, collision category and enabled state. No self-intersections or zero-area polygons. Surface: stable surface_id, walkable polygon and deterministic height function/mesh, floor group and permitted slope/step metadata. Connection: from/to surface_id, endpoints, enabled condition and width. Numeric slope/step limits must match motor configuration, not be chosen independently by environment.

Planned shared collision categories use bit positions: 1 world solid, 2 player body, 3 enemy body, 4 ally body, 5 interaction sensor, 6 hurtbox, 7 attack hitbox. Bodies query world plus explicitly configured body categories; attack hitboxes query hurtboxes and then faction/height/obstruction rules; sensors never block motion. Additional categories require integration assignment. This assignment is not yet installed in any project settings.

BLOCK01 invariants: preserve 12 m road, 4 m sidewalks, 8 m cross street, 4.8 m roof, south/north stairs, alley bypass and north exit. Gate street route requires panel; roof/alley do not. Gate state machine `closed → opening → open`; `open` becomes authoritative only when collision permits crossing. Until open, collision remains enabled. Existing B1 threshold is gate > .96; use as parity reference while choosing a final animation. Save/checkpoint stores stable terminal state, not a half-lift pose. Loading `open` restores art/collision/navigation together. Duplicate use does not retrigger unlock or rewards. Roof/ground remain distinct floor groups even at matching screen coordinates.

## 6. Gameplay, missions, saves and input

Required action IDs: `move` (normalized 2D vector), `run`, `dash`, `interact`, `map`, `pause`. Conditional D07 actions: `attack_light`, `attack_heavy`, `guard`, `counter`, `weapon_next`, `heal`; conditional D11 `jump`. Bind physical keys/touch buttons only after conflict review. Pause/modal/focus loss/pointer cancellation clears held actions and cancels pending transient input. Debug rotate is separate from shipping action map. Gamepad support is not assumed.

Interaction request contains actor instance, target interaction ID and action instance. Gameplay checks distance, height, floor, prerequisites and whether used; environment supplies anchors/state visuals. Encounter lifecycle is `inactive → active → resolved` or `failed → reset`; owns spawn-instance IDs. Completion event is keyed by encounter_id/run_id and emitted once; reset removes old instances before restoring checkpoint. AI chooses commands via the motor/combat APIs and obeys navigation gates/floors.

Mission state is `locked`, `available`, `active`, `completed` or `failed`, scoped to stable MIS ID and era. Required vs optional objectives are explicit. Narrative scene outcome is separate from retryable player death. Scene skip applies required outcome flags once and restores input/camera; it cannot invent a different story result. Story approval defines outcomes, not the animation producer.

Save envelope version 1 fields: `save_version`, `content_revision`, `campaign_id`, `active_context_id`, `contexts`, `checkpoint_id`, `completed_scene_ids`. Each context contains `era`, map_id/spawn_id, player state, approved weapon progression, mission states, encounter states, gate states and optional flags. Present-day and flashback contexts have separate keys; transition declares which approved outcomes transfer, default none. Settings have their own versioned record and never overwrite campaign progress.

Writes validate then replace the last good save atomically where the platform allows; retain a last-good backup. Unknown schema/content versions cannot silently load into the wrong map. Corrupt/denied storage presents a recoverable message and leaves current session/last-good save intact. Migration code needs fixtures for each supported prior version. Do not serialize transient node paths, animation frame indices, source absolute paths or half-open hit windows. Retry reconstructs from checkpoint without replaying rewards/cues. Final completion has a stable once-only flag and an approved resume policy (D12).

## 7. Manifest schema and readiness

Both CSVs use UTF-8, one header, comma delimiter and proper CSV quoting; semicolons separate ID lists inside cells. Empty means **unknown/not available**, never zero. Booleans are lowercase `true`/`false`. Hashes identify bytes, not creative approval. Paths with aliases resolve using TECH_SPEC; planned paths are kept in a distinct column and are not existence claims.

Animation CSV: `animation_id` is unique across requirement and source rows; `record_type` is `requirement` or `source_clip`; `requirement_ids` links source to ANM rows; `actor_ids`, scope, label, owner and status identify scope. `source_root/source_path/source_action/source_sha256` identify external evidence; `rig_id`, `fps`, playback/key bounds, closing key, duration, loop and motion describe authored data; yaw remains source degrees. `candidate_ids` links requirement to source, never marks fulfillment. `export_path` is blank until a file exists; `planned_export_path` is only a destination. `events_status`, `qa_status`, `qa_ref`, `engine_ready`, `dependencies` and `notes` expose blockers.

Environment CSV: unique ENV ID plus family, scope and LOC/MIS lists; `source_root/source_path/source_ref/source_sha256` identify evidence; `status` separates `prototype_geometry_external`, `planned_blocked` and `conditional`; `representation_target` is modular 2D/layers, not acceptance of current visible 3D. `camera_profile`, `module_count`, `pixels_per_metre`, `world_dimensions_m`, `pivot_rule`, `collision_height_rule`, `export_path`, `planned_asset_dir`, dependencies and QA describe handoff. Unknown quantities stay empty. ENV041/042 are treatment packages and ENV044 a gate presentation package, not invented image counts.

Before promotion validate uniqueness, known foreign IDs, file/hash match, frame/duration math, dependency closure, compatible rig/camera/schema versions, required events and documented tests. Rejected or diagnostic clips cannot satisfy requirements. The lead updates the board only after both source and consumer evidence pass.
