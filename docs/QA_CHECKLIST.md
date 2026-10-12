# QA checklist and current evidence

Version 1.0 • 12 October 2026. Use the relevant checks before each task handoff, then cross-system checks before integration. Record PASS / FAIL / NOT RUN / BLOCKED separately. A missing dependency is not PASS. Every report includes task/branch/base/head, source and export hashes, exact commands, engine/tool versions, device/browser, observed results and reproducible failures. Historical QA is labeled historical.

## Documentation setup results

| Check | Result and limit |
| --- | --- |
| Four source documents read | Game Bible, Art Bible, Acts and Maps read from GitHub root; Gameplay Systems from earlier workspace. Byte-identical copies created under `docs/`; originals retained. |
| Test document deletion | Removed untracked `connection-test.html` in GitHub root, as requested. It was never in Git, so deletion is not a tracked diff. |
| Blender read-only inventory | PASS: A1 opened with Blender 5.2.1 LTS; 37 bones, 32 deform, 22,449 vertices, 17,801 polygons, packed 2048² image; 11 Ronin actions plus diagnostic. Action records equal earlier inventory. See [BLENDER_LIBRARY.json](inspection/BLENDER_LIBRARY.json). No source save or pose rebuild. |
| HTML source syntax | PASS: extracted B1 inline JavaScript checked with `node --check`; no implementation edits. Not a renderer, gameplay or phone test. |
| Original Godot G0 | FAIL: Godot 4.6.2 import reports `world.gd:112`, expected `in` or `:` after loop variable. Original preserved. |
| Corrected Godot G3 | Limited PASS: temporary copy imports with no script parse errors and launches 60 headless frames without script/runtime game errors. No visual, route, collision, export or device certification. |
| Test environment warnings | Godot editor could not save sandbox-protected user editor settings. Runtime reported macOS certificate-store warning. These are not hidden as a clean all-log pass. No permission/settings changes made. |
| Preservation / manifests / links | See [SETUP_VALIDATION.json](inspection/SETUP_VALIDATION.json): original byte hashes, copy equality, expected scope, CSV IDs/ranges/references, board dependency DAG and local links checked. |
| Git whitespace check | New authored files pass. The four byte-identical source copies retain eight intentional Markdown hard breaks (two trailing spaces each); these are the only inherited whitespace exceptions. |
| Full game / animation export / final art | NOT RUN / NOT AVAILABLE: no assembled runtime in Git, no accepted GLB, no final 2D environment kit. No fresh full Blender pose sampling or browser playthrough. |

Raw scoped Godot/JavaScript test output is retained in [RUNTIME_CHECKS.txt](inspection/RUNTIME_CHECKS.txt); source file hashes are in [PROJECT_INVENTORY.json](inspection/PROJECT_INVENTORY.json). The setup validation report defines precisely what was compared.

## Preservation and repository gate — every task

- [ ] Inspect branch/worktree and unrelated edits; record base commit and allowed paths.
- [ ] Hash inputs before and after; no unexpected changes to original code, Blender libraries, motion sources, textures or references.
- [ ] Diff stays within ownership/task scope; no rebuild, rename, relocation, mass formatting or unrelated repair hidden in a feature change.
- [ ] Source/export/provenance dependencies are present and hash-verified in a clean checkout or explicitly retrieved artifact store.
- [ ] `git diff --check` passes (document intentional inherited formatting exceptions when preserving unchanged references); manifest IDs are unique, references valid and required fields populated for claimed readiness.
- [ ] New tools resolve paths from the worktree; a dry run cannot save into the legacy workspace or another agent's checkout.
- [ ] No binary conflict resolved by blind ours/theirs; preserve both versions and record reconciliation.
- [ ] Commit contains exact assigned files; README/run instructions match actual executable content. A placeholder directory cannot pass startup.

## Character and animation gate

- [ ] Selected CHR ID and era match approved reference; standard/elite/Foot colors and silhouette remain distinct.
- [ ] Source mesh/UV/material/rest pose/bone hierarchy and unaffected action hashes match baseline; intended changes are listed explicitly.
- [ ] Textures resolve without personal absolute paths; unit height, up/forward axes, foot origin and root scale agree after import.
- [ ] Bake IK/constraints on derivative; source controls remain intact. Root motion survives removal of control-only export bones.
- [ ] Inspect normal speed, slow motion and between-frame poses: grounded soles, knee direction, foot recovery hitch, elbow spread, shell/cloak/shoulder intersections and seams.
- [ ] Preserve corrected Sad Walk and narrowed run arms; no Mutant Walking or diagnostic action in runtime export.
- [ ] Loop closing pose/time, accumulated root travel, turn heading and one-shot return pose obey manifest. No duplicate closing-frame event.
- [ ] Skinning comparison covers six-influence shoulder/cloth region and preserve-volume differences; any pruning/bake conversion has measured evidence.
- [ ] Extreme Punch/Jump poses receive visual review of known shoulder stretch; old ~5.5× local edge ratio is a limitation, not a universal acceptance threshold.
- [ ] Test idle→walk→run→stop, turns both directions, all approved attack/reaction/interact transitions, cancellation and variable playback speeds on the actual rig.
- [ ] Root-motion collision test stops at wall/gate and preserves final yaw; no doubled travel or snap at loop/retry/transition.
- [ ] Weapon sockets/grips align in relevant poses; no implied finger animation. Jump is only wired if D11 approves it.
- [ ] Exact export/import comparison and fixed-camera preview recorded before `engine_ready=true`; Blender QA alone cannot set it.

For new measured geometry checks, report sampling interval and minimum sole distance/IK/seam/loop errors in metres plus clear display units. Existing near-zero historical values are regression evidence, not a promise of equivalent export precision. Choose and record an acceptance tolerance in the task before measuring; unresolved visual/precision tradeoffs prevent acceptance.

## Environment / 2D composite gate

- [ ] Every piece resolves ENV/module ID, source/export/hash, camera profile, pivot, pixel/world scale, bounds, layer and dependencies.
- [ ] Lossless alpha edges, seams, cropping, atlas padding if used, normals/lighting assumptions and contact shadows look correct at actual desktop/phone scale.
- [ ] Real 3D actor stays correctly in front/behind art, under foreground occluders, on roof/stairs and within cutaways. No unsupported camera rotation or billboard view exposes missing art.
- [ ] Explicit collision/height/navigation data matches visible art; decorative doors, skyline, manholes and fire escapes do not become unintended gameplay.
- [ ] Street, roof and alley each reach the BLOCK01 exit from fresh state; repeat in both directions where permitted. Ground bypass never requires gate release.
- [ ] Closed gate blocks; opening remains blocked until clear; open art/collision/nav agree; repeated use, reload and retry are idempotent.
- [ ] Roof remains 4.8 m; stairs are continuous, edges/rails prevent unintended falls, facade changes do not narrow route clearance.
- [ ] Ground actors cannot hit/reach roof targets through screen overlap; shared X/Z with different Y resolves to correct surface.
- [ ] Rain/shadow/foreground effects do not conceal attacks, route cues, prompts or touch controls.
- [ ] Later-act kits contain only approved pieces; unknown location/module counts remain blocked, never silently zero.

## Gameplay and state gate

- [ ] Diagonal movement normalized; walk/run/dash and stairs stable at low/high render rates; collision sweep/substeps prevent tunneling.
- [ ] Keyboard and touch actions agree; blur, modal, pause, pointer cancellation and resume do not leave movement/guard/run stuck.
- [ ] Attack events fire in order once when a tick crosses multiple markers, at time zero and across loop wrap. Seeking/loading cannot replay damage.
- [ ] Only active windows damage; once-per-target/window limits hold; walls, floor, factions and death state block invalid hits.
- [ ] Approved guard/counter front/rear rules, resources and cancel windows pass boundary-time tests; all hitboxes close on interruption.
- [ ] Enemy spawn/engage/attack/recover/defeat/reset works once per lifecycle. No duplicate spawns, rewards or endless encounter activation after retry.
- [ ] Mission prerequisites are explicit, optional content does not block required progress, exit targets resolve and completion fires once.
- [ ] Scene enter/skip/end restores controls/camera/subtitles correctly and applies required outcome exactly once.
- [ ] Save/load before and after gate, encounter, mission, map/era and finale transitions preserves intended state. Settings and campaign records remain separate.
- [ ] Corrupt save, denied storage, full storage, unknown version/content revision and interrupted writes recover without silently destroying last-good progress.
- [ ] Present-day and flashback inventory/health/flags remain isolated; only approved transition outcomes transfer.
- [ ] Defeat blocks actions; retry restores checkpoint, not transient animation/hit windows. Scripted story loss is distinct from ordinary failure.
- [ ] Retained healing/caches cannot overheal or duplicate inventory; unapproved mechanics are absent.

## Build, migration, performance and accessibility gate

- [ ] Exact Godot executable/build, renderer and export template versions recorded; clean checkout imports and starts without script errors. Inspect logs even when exit code is zero.
- [ ] Run corrected source candidate, not an older similarly named folder. Existing G0 parse defect is not misreported as fixed by documentation.
- [ ] Accepted browser revision and Godot build share map/actor/mission IDs, action semantics, event ordering and state outcomes; compare all three routes and M1 encounter/retry fixtures.
- [ ] Actual skinned model and 2D kit work in chosen targets; missing required assets fail clearly. No personal-path dependencies or implicit Blender install required for player builds.
- [ ] Exported build opens independently of editor; browser hosting paths and asset case work on a clean machine. Developer QA hooks/debug rotation are absent or gated in release.
- [ ] D09 names real devices/browsers, resolution, sustained frame-time/FPS, memory, load-time and texture budgets. Record cold/warm load and sustained rain/combat cases against those values.
- [ ] A headless run, emulation or software-rendered browser does not substitute for hardware performance and visual checks.
- [ ] Touch targets/readability, subtitles/contrast, pause behavior, mute persistence and approved reduced-effects options pass at target aspect ratios.
- [ ] Required audio starts after web user gesture; cue timing agrees with authoritative events and is still understandable when muted where specified.

## Content completion gate: each act and entire campaign

| Scope | Required coverage before DONE |
| --- | --- |
| M1 / BLOCK01 | Final hybrid art + real actor, three routes, approved combat/encounter, MIS01 exit, approved MIS02 optional content, retry/save, desktop/touch and D09 budgets. Traversal alone fails this gate. |
| FAMILY | MIS03–04, approved LOC16 maps and family-era actors, training/teamwork, companion recovery, story and context transitions. |
| FALL | MIS05–07 / LOC17–19, all three loss packages, controlled roles, scripted outcomes vs retry, scene skip and flashback isolation. |
| LOST | MIS08–10 / LOC20 approved journey locations, weapon mastery, narrative transitions and earned-unlock persistence. No invented survival systems. |
| RETURN | MIS11–13 / LOC21–22 and approved BLOCK01 placement; district/ally/optional-content coverage, actors, combat, exits and saved flags. |
| FINAL | MIS14–17 / LOC23–24 approach/escalation, approved Hiroto phases, closure and stable post-completion reload. Skyline art does not count as a level. |
| Conditional prologue | MIS18 / LOC25 only if approved; then failure/rescue and chronology handoff receive the same acceptance. Otherwise explicit exclusion. |
| Entire campaign | Every approved map/scene/mission/actor/clip/transition is mapped to delivered content and evidence; no omitted arc or unresolved required dependency; clean build/export and save migrations pass. |

## Regression scope

Run checks affected by the change and required consumer gates. Do not rebuild or rerun every historical animation script for a documentation change. For clip changes, retest that clip, affected transitions and preserved source actions; for collision/art changes, retest impacted routes/height/occlusion; for schema/save changes, run all supported migration fixtures. New failures remain open on the board with reproducible steps. Only the lead marks shared integration complete after producer and consumer evidence agree.
