# GAMEPLAY SYSTEMS

**Project:** Last Ronin Project  
**Version:** 1.0 — evidence consolidation, 12 October 2026  
**Owner of creative decisions:** Kevin Graham

## Authority and evidence labels

This document preserves the recoverable project, including all five story arcs. It does not invent missing story, maps, dialogue, boss phases, or numerical tuning. Full verbatim transcripts were not available through retrieval; 52 current project-folder files were inventoried, the latest production package and block source were read, selected art was visually inspected, and prior conversation context was retrieved. A complete approved screenplay and complete chapter list were not found.

- **LOCKED:** explicit current user instruction or recovered user decision.
- **RECOVERED PLAN:** prior narrative/design plan; detailed approval may not be recoverable.
- **PROTOTYPE:** behavior or content in an existing build; existence does not establish final design approval.
- **LEGACY:** earlier Hollow Signal experiment; reusable reference, not automatic campaign canon.
- **TBD:** missing, conflicting, or insufficiently specified.
- **PRODUCTION REQUIREMENT:** implementation/handoff criterion derived from the chosen direction, not a newly approved creative feature.

Current instructions override older prototype behavior: fixed orthographic camera, graphic-novel art, 3D characters, modular 2D environments. Keep the whole campaign in scope. The first production milestone is one complete playable city block; it is not the whole game.

## Source register

| Source | Material | Use and limit |
| --- | --- | --- |
| U0 | Current request, 12 October 2026 | Locks four-document scope and visual representation |
| C1 | The Last Ronin, 10–11 October; retrieved conversation context | Earlier Hollow Signal experiment and orthographic correction |
| C2 | Last Ronin Game Direction, 11–12 October; retrieved context | Story-first Michelangelo adaptation, five story arcs, character production, later return-first proposal; not a full transcript |
| C3 | Production planning and Game Building Comparison, 12 October; retrieved context | All-act scope, first playable block, 3DAIStudio/Blender/Mixamo and hybrid environment intent |
| P1 | Last_Ronin_Production_Package.zip, created 12 October 2026 | Read source review, scope inventory, asset manifests and integration contracts; secondary compilation, not independent creative approval |
| B1 | Last_Ronin_Act1_Block01_v02.html and Last_Ronin_Block01_v02_Source_and_QA.zip | Current inspected traversal source and historical QA; not a completed combat game |
| L1 | hollow_signal_orthographic_computer.html; earlier phone/desktop counterparts cataloged | Earlier separate combat experiment |
| R1 | Last Ronin Michelangelo Turnaround.png | Visually inspected hooded character reference |
| R2 | Rainy Neon Cathedral Showdown.png; Rainlit Chains: Neon City Showdown.png | Visually inspected early city mood references; generated names/signage are not approved geography |
| R3 | Last_Ronin_Block01_v02_Roof.png | Visually inspected layout/blockout evidence; not final-art approval |
| R4 | Sci-Fi Robot Soldier Turnaround.png; Futuristic Red-Visor Synth Soldier Turnaround.png; Armored Ninja Turnaround Sheet.png | Visually inspected blue-gray, white/red, and purple-accent designs |

The production package catalogs other turnarounds and model screenshots. Their identity mappings are secondary evidence here unless specifically resolved below. No usable rigged model/export or final animation was recovered. No runtime QA was rerun for this documentation task. Do not read historical QA counts as fresh certification.

## Design and implementation baseline

The recovered design is narrative action-adventure with connected areas, optional exploration and deliberate directional melee/counterplay. Walk/run/dash, grounded elevation, interactions and route choice exist in the current city-block prototype. Combat exists in an earlier separate Hollow Signal experiment; it is not integrated into the current block.

| Area | Current B1 | Legacy L1 | Campaign status |
| --- | --- | --- | --- |
| Movement | Walk/run/dash; camera-relative; stairs/roof grounding | Two-axis movement and dodge | Preserve traversal; final combat motion contract TBD |
| Camera | Orthographic with tuning/rotation | Angled overhead | U0 locks fixed orientation; remove unsupported release rotation |
| Combat | Absent | Combo/heavy/guard/perfect-block, stamina | Intent recovered; final retained move list and tuning TBD |
| AI | Atmospheric stand-ins, no enemy combat AI | Melee, shield, drone and Gatekeeper behaviors | Map approved actor roster to authored AI; do not infer mappings |
| Interactions | Gate, notes, exit | Caches/checkpoints/terminal | Current interactions known; final campaign content TBD |
| Progression | No campaign progression | Local demo progression/checkpoints | Weapon mastery and story progression planned |
| Persistence | Settings persistence, not campaign save | Checkpoint behavior in separate demo | Durable campaign save not established |
| Story | Draft notes and completion modal | Different original setting | Full story sequencing absent |

The browser baseline is raw single-file WebGL2/JavaScript. A later Three.js/Sprite3D suggestion is not an implemented conversion. Earlier Godot blockouts are not synchronized ports. Exact final runtime/version is D05.

## Movement and traversal

**PROTOTYPE:** camera-relative two-axis movement, normalized diagonal input, walk/run, dash using last movement direction, collision, gravity/ground snapping, stairs and roof height. B1's run multiplier is 1.65; dash speed 12 world units/second, duration 0.23 seconds and cooldown 0.80 seconds. These source values are diagnostic references, not locked balancing decisions.

**PRODUCTION REQUIREMENTS:** feet remain grounded on each permitted surface; walls/gates stop movement; dash cannot tunnel through obstacles; stairs connect continuously to the roof; navigation distinguishes ground and roof. Final actor animation and collision must remain separate so model replacement cannot change level traversal.

**TBD:** final speed/acceleration, turn responsiveness, dodge versus dash distinction, invulnerability, stamina cost, cancellation and root motion. Jump, free climbing, ledge hang, vault, stealth and takedowns are not established requirements. A roof route using stairs does not approve parkour.

## Input and target parity

| Action | Current block binding | Status |
| --- | --- | --- |
| Move | WASD/arrows; touch joystick | Prototype baseline |
| Run | Shift; touch Run | Prototype baseline |
| Dash | Space; touch Dash | Prototype baseline |
| Interact | E; touch Use | Prototype baseline |
| Map | M / UI | Prototype baseline |
| Pause/close | Esc / UI; source also supports P | Prototype baseline |
| Rotate camera | Q/R | Inspection feature; conflicts with fixed shipping direction |
| Zoom / tuning | Wheel / T | Debug/reference behavior; shipping availability TBD |
| Light/heavy/guard/counter/weapon switch/heal | Not present in B1 | Final unified bindings TBD |

Legacy combat bindings must be reconciled with B1 rather than copied over existing actions. All required actions need desktop and touch equivalents. Losing focus, pointer cancellation, opening a modal and pausing must clear held inputs. No gamepad commitment was recovered.

## Combat

**RECOVERED PLAN:** directional melee, deliberate attack commitment and counterplay; four weapon families connected to the brothers. **LEGACY:** combos, heavy attacks, guard, perfect block, stamina, shield-break interactions and damage feedback. **TBD:** which exact legacy mechanics carry forward, values and cancel rules.

| Weapon family | Recovered narrative association | Mechanics not specified |
| --- | --- | --- |
| Nunchaku | Michelangelo | Move list, timing, reach and resource use |
| Sai | Raphael | Move list, guard/counter behavior and differentiation |
| Bo staff | Donatello | Range, arcs and crowd interaction |
| Katanas | Leonardo | Move list, equip form and damage rules |

Do not assign invented damage numbers, bonuses or archetypes to these weapons. Carrying all brothers' weapons in story does not specify starting gameplay access or switching rules.

Production combat contract: each attack needs startup/active/recovery timing, facing rules, hit volume and height band, per-target hit limits, resource cost, interruption/cancellation, animation events, audio/VFX and damage response. Active damage must not come from every rendered frame. Walls and floor separation must prevent invalid hits. Guard direction, parry window and counter reward need explicit definitions before animation timing is finalized.

## Health, resources, defeat and retry

Health and damage response are necessary for the planned combat, but final capacities, healing economy, stamina regeneration and difficulty rules are TBD. Legacy healing/caches are reference mechanics, not automatic campaign loot scope. No XP level curve, currency, skill tree or equipment rarity system was recovered.

Defeat must stop conflicting input and restore an authoritative checkpoint state without duplicate spawns/rewards. Story-required loss sequences need a distinct outcome from ordinary player death; exact handling is D12. Resource values cannot be finalized from the traversal-only block.

## Progression and chronology

**RECOVERED PLAN:** authored story progression through the five arcs; mastery of the brothers' weapons in LOST; optional exploration/secrets in RETURN. Unlock conditions, challenge design and rewards remain TBD.

**PRODUCTION REQUIREMENT:** separate present-day progress from flashback state. A flashback must not accidentally grant, remove or duplicate present-day inventory/health/story flags. Track stable mission/actor/area IDs and define chapter transitions after D01. Brother memories may serve narrative presentation; no mechanical memory-buff system is assumed.

## Enemy and companion AI
| ID | Type | Actor | Behavior evidence | Scope | Status | Task |
| --- | --- | --- | --- | --- | --- | --- |
| EN01 | Standard Synja Patrol | CHR03 | Approved roster; attack/detection rules missing | TBD via encounter map | Blocked; no final behavior verified | G-EN01 |
| EN02 | Foot Bot | CHR04 | Approved roster; distinct behavior missing | TBD via encounter map | Blocked; no final behavior verified | G-EN02 |
| EN03 | Elite Synja Patrol | CHR05 | Approved roster; distinction from standard missing | TBD via encounter map | Blocked; no final behavior verified | G-EN03 |
| EN04 | Large Mouser Combat Robot | CHR08 | Approved asset; miniboss/combat rules unresolved | TBD via encounter map | Blocked; no final behavior verified | G-EN04 |
| EN05 | Flying Mouser | CHR09 | Approved asset; flight/detection/attack rules unresolved | TBD via encounter map | Blocked; no final behavior verified | G-EN05 |
| EN06 | Flying Foot Patrol Vehicle | CHR07 | Current atmospheric stand-in; combat status unresolved | TBD via encounter map | Blocked; no final behavior verified | G-EN06 |
| EN07 | Oroku Hiroto | CHR02 | Final boss; phase design missing | V | Blocked; no final behavior verified | G-EN07 |
| EN08 | Karai | CHR15 | Confrontation participant; player-facing boss role unresolved | II | Blocked; no final behavior verified | G-EN08 |
| EN09 | Baxter attack forces | CHR16 | Attack in story; enemy composition missing | II | Blocked; no final behavior verified | G-EN09 |
| LEG01 | Melee patrol | Unmapped legacy actor | Chase; directional slash; windup/strike/recovery | Hollow Signal only | Legacy source exists; no campaign adoption inferred | G002 |
| LEG02 | Shield unit | Unmapped legacy actor | Frontal protection; heavy hit breaks armor; legacy mapping to Synja unapproved | Hollow Signal only | Legacy source exists; no campaign adoption inferred | G002 |
| LEG03 | Surveillance drone | Unmapped legacy actor | Ranged shot; distance management; not automatically Flying Mouser | Hollow Signal only | Legacy source exists; no campaign adoption inferred | G002 |
| LEG04 | Gatekeeper / Series 09 | Unmapped legacy actor | Slash, radial slam, charge; not automatically Hiroto or Large Mouser | Hollow Signal only | Legacy source exists; no campaign adoption inferred | G002 |

### AI implementation requirements

For every approved enemy specify perception, engagement range, path constraints, attack selection, telegraph/strike/recovery, stagger/defeat, disengagement and reset. These are contracts to complete, not invented behavior values. Define attack permissions across elevation and obstruction. An enemy must not strike the roof from street level because a screen-space overlap occurs.

Legacy melee chase/slash, shield defense, drone distance management/projectiles and Gatekeeper slash/slam/charge can inform implementation. None are automatically assigned to a Synja, Flying Mouser, Large Mouser or Hiroto. Surveillance vehicles are not automatically fightable.

Family teamwork with AI-controlled brothers is recovered scope. Following, regrouping and authored participation need to be specified. Ally combat, resurrection, escort fail states, squad commands and Casey Marie playability are TBD. Scenes must not deadlock because a companion cannot reach an interaction.

## Interactions, encounters and objectives

B1 chooses nearby interactions using horizontal distance plus a height filter (1.25 world units in the source). Gate use opens the checkpoint once; bypass routes do not require gate release. Draft notes show modal text; the north exit marks the environment pass complete. There is no authored tower assault behind that trigger.

Each campaign interaction needs range/height rules, input, prerequisites, one-time/repeatable status, state changes, feedback and persistence. Separate decorative doors and manholes from usable entrances. Define encounter spawn, activation, clear/failure/reset and mission coupling. Optional memories must not block the main objective unless specifically approved.

## Dialogue, memories and cinematic sequences

The narrative needs defined speakers, dialogue text, scene triggers, camera treatment, control locking and restoration, subtitles, skip/replay and resulting story flags. Exact presentation and voice/audio scope are TBD. Skipping a scene must apply its required state changes once. The draft diner text is not a finished script. No dialogue choices or branching narrative are assumed.

## Save and load

Campaign persistence is not established in B1. The production requirement is a versioned state with current location/spawn, story era, mission state, approved weapon progression, player state, encounter/gate states and optional-content flags. The precise schema is not yet approved. Settings must remain separate from campaign progression.

Validate resume before/after mission transitions, corrupt/denied storage, version mismatch, death/retry and finale completion. Do not treat exporting the prototype's camera/settings JSON as a campaign save.

## UI, audio, effects and accessibility

Maps, destination cues, interaction prompts and pause/settings exist as prototype UI. Health/resource and combat feedback require integration. Preserve readability on phone and desktop; exact HUD layout and typography are not finalized. Debug tuning panels are not a release UI requirement.

Rain/atmosphere is a visual direction. Legacy synthesized audio does not establish a final soundtrack, voice cast or sound library. Footsteps, attacks, impacts and warnings must follow actual gameplay events if included. Subtitle/caption rules, audio mix, reduced-effects options and performance settings remain D10/D09 decisions.

## Full system inventory and objective implementation criteria

The following 24 system rows preserve the production package's scope. “Source present, not integrated” means a component exists in a prototype or reference; it does not claim that the complete campaign system works. Acceptance statements are production criteria, not claims of completed tests.
| ID | System | Evidence | Status | Deliverable | Acceptance | Task |
| --- | --- | --- | --- | --- | --- | --- |
| SYS01 | Camera-relative movement and grounding | S01 existing | Source present, not integrated | Walk/run/dash, diagonal normalization, stairs and roof surfaces | Route tests pass with grounded feet; dash cannot tunnel through walls or fall through roof. | G-SYS01 |
| SYS02 | Orthographic camera and occlusion | S01 existing | Source present, not integrated | Locked gameplay preset, approved camera options, cutaway and follow behavior | Player and route remain readable behind each facade; no unsupported camera angle exposes missing art. | G-SYS02 |
| SYS03 | Collision and navigation | S01/S02 separate | Not established in latest block | Shared footprints, height-aware pathing and actor separation | Ground enemies do not hit across roof height; navigation reaches allowed targets and never crosses blocked gates. | G-SYS03 |
| SYS04 | Input and desktop/touch parity | S01/S02 conflicting | Not established in latest block | Unified actions and bindings; touchscreen combat affordances | Every required action works on both targets; Q/E/R/Shift conflicts resolved; pointer cancellation and blur clear held actions. | G-SYS04 |
| SYS05 | Interactions and gate state | S01 existing | Source present, not integrated | Gate control, inspection, range/height filters and idempotent use | Closed gate blocks; opening allows crossing; repeated use does not corrupt state; bypass routes do not require gate. | G-SYS05 |
| SYS06 | Directional melee and combos | S02 legacy / S04 intent | Source present, not integrated | Approved attack list, facing and damage windows | Only active windows damage; each swing hits each target at most once; walls and elevation block invalid hits. | G-SYS06 |
| SYS07 | Guard, timed counter and damage response | S02 legacy / S04 intent | Source present, not integrated | Guard/counter rules, reaction events and tuning data | Front/rear tests obey agreed rule; successful counter has one damage event; stun exits cleanly. | G-SYS07 |
| SYS08 | Dash / avoidance and resource rules | S01/S02 conflict | Not established in latest block | Approved dash, invulnerability, cooldown and stamina policy | No infinite dash or unintended immunity; resource limits and cancellation match contract. | G-SYS08 |
| SYS09 | Enemy behavior and encounter lifecycle | S02 reference; absent S01 | Source present, not integrated | Spawn, detect/engage, attack/recover, defeat/reset, route-aware navigation | Approved M1 encounter starts once, resets correctly after failure and cannot softlock either bypass route. | G-SYS09 |
| SYS10 | Health, defeat and retry | S02 reference; absent S01 | Source present, not integrated | Damage/death state and checkpoint restore | No input after death; retry restores authoritative mission/enemy/gate state with no duplicate rewards. | G-SYS10 |
| SYS11 | Supply caches and healing | S02 legacy; approval pending | Source present, not integrated | Approved item policy, cache state and use feedback | If retained: no overheal, duplicate cache pickup or negative inventory after reload; otherwise explicitly excluded. | G-SYS11 |
| SYS12 | Mission and story state | S01 exit only | Not established in latest block | Data-driven objectives, optional flags, failures and chapter transitions | Every prerequisite is testable; completion fires once; optional memory cannot block main objective unless explicitly approved. | G-SYS12 |
| SYS13 | Save, load and version migration | S02 checkpoint only | Not established in latest block | Versioned campaign state separate from settings | Fresh start, resume, denied storage, corrupt payload and version mismatch all recover without silent progress loss. | G-SYS13 |
| SYS14 | Dialogue and cinematic sequencing | Absent S01 | Not established in latest block | Speaker IDs, subtitles, interaction lock, skip/replay and restoration | Scenes enter/exit with correct control state; skip applies required story flags once and cannot deadlock progression. | G-SYS14 |
| SYS15 | Brother / companion AI | S04 Act I | Not established in latest block | Follow, regroup and authored teamwork actions | Each approved brother participates; separation/route reset never stalls objectives; no new playable roles assumed. | G-SYS15 |
| SYS16 | Weapon mastery and progression | S04 Act III | Not established in latest block | Approved weapon states, unlocks and animation binding | Every approved mastery objective unlocks intended state once; load/retry retains only earned progression. | G-SYS16 |
| SYS17 | Connected areas and chronology transitions | S04 | Not established in latest block | Act/chapter graph, spawn handoff and flashback state separation | Each edge works forward and on reload; present-day and flashback inventory/flags do not leak. | G-SYS17 |
| SYS18 | HUD, map and diegetic route cues | S01/S02 | Not established in latest block | Accessible health/combat feedback, readable signs and current objective | No debug overlay in release; mission wording matches current state; touch controls do not cover essential cues. | G-SYS18 |
| SYS19 | Audio and visual combat feedback | S02 synthetic reference | Source present, not integrated | Approved footsteps, rain/ambience, attack/impact cues and subtitle policy | Mute persists; audio starts after gesture; cues align with gameplay events; warnings remain readable over rain. | G-SYS19 |
| SYS20 | Settings, pause and failure diagnostics | S01 existing | Source present, not integrated | Settings import/export, pause, render options and WebGL failure UI | Invalid imports rejected safely; pause halts gameplay; denied storage/fullscreen does not crash. | G-SYS20 |
| SYS21 | Model and animation adapter | Absent S01 | Not established in latest block | Stable actor wrapper, skeleton binding, sockets and replacement procedure | One representative real model can replace a stand-in without changing movement, mission or combat code; missing model uses labeled placeholder. | G-SYS21 |
| SYS22 | Rendering and asset streaming/budgets | S01 procedural | Not established in latest block | Approved 2D/3D compositing, depth, rain, shadows and asset loading | Correct ground contact and occlusion at approved views; no missing assets; agreed D09 budget met. | G-SYS22 |
| SYS23 | Godot delivery / parity | S05 older blockout | Not established in latest block | Target Godot import, actions, scenes and browser behavior parity map | Exact approved Godot version imports and launches without script errors; same M1 objective/routes/combat contract pass. | G-SYS23 |
| SYS24 | Final boss and campaign completion | S04 | Not established in latest block | Hiroto behavior from approved brief plus ending flags | All approved phases reachable and recoverable; story outcome/ending fires once; reload cannot trap player after finale. | G-SYS24 |

## Integration contracts

| Boundary | Required information | Check |
| --- | --- | --- |
| User model to controller | Actor ID, scale, axes, skeleton, material and sockets; separate visual mesh | Swap a stand-in without rewriting mission/AI/movement |
| Animation to combat | Clip/rig version, motion policy, hit/interaction events, transition and cancel rules | One action produces the intended events once |
| 2D art to 3D actors | Fixed projection, pixel/world scale, depth masks, ground and height surfaces | Feet, shadows and front/behind order agree |
| Map to navigation | Collision, walkable heights, route links and gate state | All approved paths are reachable, wrong-floor paths blocked |
| Encounter to mission | Actor IDs, triggers, clear/failure/reset rules | No repeated completion or permanent lock |
| Story to save | Era, scene outcome, transition and optional flags | Flashback/current-state isolation and safe resume |
| Browser to Godot | Same input/mission/combat semantics and asset contracts | Equivalent segment acceptance, not just a successful import |

## Whole-campaign completion criteria

Each recovered story package needs an authored mission/scene implementation and explicit completion state. Every approved enemy requires behavior and animation, every map requires collision/navigation and hybrid art, every transition requires state/save behavior, and the finale requires a tested ending. An Act I title screen, 13-chapter claim, or environment-only block does not satisfy this gate.

M1 is a complete city-block integration test. Remaining blockers are D01 chronology; D03 actual models; D04 encounter/story brief; D05 runtime/source baseline; D06 full maps/scripts; D07 combat/animation decisions; D08 role/era mappings; D09 performance targets; D10 audio/presentation; D11 expanded traversal if required; D12 finale. D02's visual representation is now locked, but its exact technical export contract remains open.

## Related documents

[GAME_BIBLE.md](GAME_BIBLE.md) owns story and roster. [ART_BIBLE.md](ART_BIBLE.md) owns visual/animation handoff. [ACTS_AND_MAPS.md](ACTS_AND_MAPS.md) owns mission/location coverage and the three-route block.
