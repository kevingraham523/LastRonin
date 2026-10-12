# ART BIBLE

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

## Locked visual direction

**Graphic-novel / comic-noir, fixed orthographic, 3D characters, modular illustrated 2D environments.** Dark, rainy, futuristic urban atmosphere; stylized rather than photorealistic. Preserve the character silhouettes, inked edge treatment, worn surfaces and dramatic value grouping demonstrated by the references. AI-assisted production must be repeatable across the campaign.

The representation is a hybrid scene: 3D characters inhabit spatially coherent areas assembled from modular 2D art. Collision, navigation and height surfaces may use invisible spatial geometry; that does not change the visible environment requirement. Earlier full procedural 3D blockouts are layout references, not a new art direction. Earlier side-view work is superseded.

## Camera contract

| Property | Authority / requirement |
| --- | --- |
| Projection | LOCKED: orthographic; no perspective shrinkage with distance |
| Orientation | LOCKED: fixed angled overhead gameplay view |
| Character movement | Two horizontal axes within that view; elevation where authored |
| Camera follow | B1 has following; permitted follow distance/framing remains to be finalized without changing fixed orientation |
| Exact yaw, pitch and scale | TBD; B1's 46-degree default pitch is a prototype value, not a signed-off asset camera |
| Rotation controls | B1 has Q/R quarter-turns and pitch tuning; these are prototype inspection controls, not approved shipping behavior |
| Zoom | Prototype mouse-wheel control exists; shipping bounds and phone framing TBD |
| Cutscenes | Camera/panel treatment TBD; do not assume free third-person cinematics |
| Occlusion | Production requirement: player and interactable routes remain legible behind foreground pieces |

Every 2D export must be authored against the same approved projection, orientation and world scale. Do not render one view and then expose its unpainted back by enabling arbitrary rotation. Fixed orientation does not mean the camera must be stationary in world space.

## Reference interpretation

| Reference | Observed visual language | What it does not approve |
| --- | --- | --- |
| Rainy Neon Cathedral Showdown.png | Elevated city composition, dark gothic massing, wet streets, cool blue and red accents, warm isolated lamps, ink-like silhouettes | A canonical cathedral district, Aurelia Spire, Velthra faction, final HUD or specific mission |
| Rainlit Chains: Neon City Showdown.png | Similar oppressive city scale, wet reflections, architectural foreground framing, readable combat clearing | Meridian/Korvex lore, River District map, shield unit placement or literal poster text |
| Last Ronin Michelangelo Turnaround.png | Olive skin, orange mask, dark hood/tattered cloak, shell, worn brown armor/straps, pale wraps and pouches; broad readable silhouette | Final rig, polycount, cloth simulation, attached weapon mesh or game-ready animation |
| Last_Ronin_Block01_v02_Roof.png | Street/roof scale, checkpoint, railings, stairs, UI/layout experiment | Final environmental texture quality, final character appearance or final camera settings |
| Three inspected enemy turnarounds | Blue-gray and white/red patrol variants; dark purple-accent Foot Bot | Final skeletons, distinct AI or final model filename mappings |

The reference images establish visual evidence. No exact final-image selection record was recovered; do not treat every generated detail as canon. Phone wallpapers outside the project are not automatically environment references.

## Style rules derived from the references

These are production interpretations of the locked direction, not new story decisions.

- Use large readable light/dark shapes before fine texture. Ink-like contours and controlled surface marks should remain readable at the game camera.
- Keep weathering selective: worn edges, torn cloth, scuffed armor and aged masonry. Do not replace illustrated surfaces with photorealistic material noise.
- Use cool desaturated city masses with restrained red security/hostile accents and localized warm lamps. Exact palette values and act-specific palettes are TBD.
- Match apparent lighting direction and shadow softness across 2D art and 3D actors. Actor contact shadows must align with the surface under their feet.
- Rain, steam and wet reflections support atmosphere without hiding combat telegraphs, stairs, exits or interaction prompts.
- Keep silhouette contrast between actors and nearby floor/background. Add depth through layers and occlusion rather than changing the projection.
- Do not impose neon rain on every historical or exile scene without an approved setting brief. Maintain the graphic-novel rendering language across distinct environments.

## Character production

The recovered pipeline is user-created 3DAIStudio models, Blender preparation/rigging and Mixamo-related animation work. Actual exports, bind poses and completed retargets were not supplied in the inspected material. A turnaround is a design reference, not proof of a usable rig. Nonhumanoid robots, flying actors, shells and capes require appropriate handling; no universal Mixamo compatibility is assumed.

Turnaround preference: wide, uncropped four-view presentation; front, left, right and rear; no weapons or extras in the base character views. Keep weapons as separately identifiable assets and define attachments in the rig handoff.

| Actor family | Preserved distinction | Missing production detail |
| --- | --- | --- |
| Michelangelo / Ronin | Hooded worn silhouette; shell and orange mask from R1 | Final export, scale, rig, cloth handling, younger variants |
| Standard Synja | Blue-gray armor with red visor/accent | Final model file and weapons |
| Elite Synja | White armor/red visor or accents | Final model file and silhouette/behavior separation |
| Foot Bot | Dark armor and purple fabric/accent | Final model file and weapon attachments |
| Hiroto | Armored-samurai candidate reference | Confirm reference mapping and final design/export |
| April / Casey Marie | Survivor/reporter reference families | Resolve exact sheets, era, rig and outfits |
| Flying Foot vehicle / Large Mouser / Flying Mouser | Separate recovered asset families | Confirm scale, articulation, flight/ground presentation and role |
| Brothers, Splinter, Karai and other story participants | Required by recovered story | Models, era variants and exact on-screen scope |

**Correction:** `Sci-Fi Robot Soldier Turnaround.png` visibly supplies the blue-gray reference; `Futuristic Red-Visor Synth Soldier Turnaround.png` supplies white/red. These correct the earlier production package's tentative reverse association. Actual user model mappings still need verification.

## Modular 2D environment construction

Separate ground, vertical structures, foreground occluders, props, animated states and distant background. Preserve existing collision and route widths when replacing BLOCK01 art. A picture alone is not a walkable surface or an interaction definition.

| Layer/family | Required handoff information |
| --- | --- |
| Ground surfaces and decals | World dimensions, tile edges, pivot, pixel scale, height plane, nonblocking/blocked classification |
| Facades and corners | Footprint, apparent height, attachment edges, foreground/depth mask, supported view |
| Roofs/stairs | Surface elevation, stair endpoints, walkable polygons, rails and edge collision |
| Props | Pivot, footprint, depth/occlusion policy, decorative versus interactable status |
| Gates/panels | Separate visual states, collision transitions, interaction anchor and animation timing |
| Skyline | Nonplayable background status; no implied accessible tower level |
| Weather/light overlays | Layer order, intensity range, animation source and readability test |

Exact raster resolution, pixels per world unit, atlas sizes, file formats, blend mode and depth technique remain TBD. Godot Sprite3D and HTML/Three.js appeared in a prior assistant pipeline recommendation; they are implementation candidates, not evidence that the current raw WebGL2 build already uses them.

## Environment family inventory

The following preserves all 52 entries in the existing manifest: 44 BLOCK01 asset/treatment families plus eight unresolved later-story kit packages. These are not 52 finished assets or a final instance count. All visible environment exports must now follow U0's modular 2D target; retain hidden collision/height metadata.

| ID | Family | Locations | Deliverable / scope |
| --- | --- | --- | --- |
| ENV001 | Road surface straight | LOC03 | Reusable asphalt tile/strip |
| ENV002 | Intersection road module | LOC04 | 8 m cross-street join |
| ENV003 | Sidewalk paving | LOC03 | 4 m sidewalk straight/end modules |
| ENV004 | Curbs and corner transitions | LOC03;LOC04 | Straight/corner curb pieces |
| ENV005 | Lane lines and transit markings | LOC03 | Separate road decals including keep-clear |
| ENV006 | Crosswalk markings | LOC04 | Worn crossing decal set |
| ENV007 | Drain grates | LOC03;LOC10 | Ground detail modules |
| ENV008 | Manhole covers | LOC03 | Ground cover module |
| ENV009 | Building shell and wall kit | LOC05;LOC06;LOC07;LOC08;LOC09;LOC12;LOC13 | Reusable walls/corners/roof-edge base |
| ENV010 | Diner facade | LOC05 | Storefront glass/shutters/door/awning/sign pieces |
| ENV011 | Residential facade | LOC06 | Lobby/window/balcony/rail pieces |
| ENV012 | Boarded tenement facade | LOC07 | Boards/service-door/window/curfew sign pieces |
| ENV013 | Service-block facade | LOC08 | Rolling shutter and maintenance signage pieces |
| ENV014 | Depot facade and roof | LOC09 | Low wall/roof/deck/edge-light pieces |
| ENV015 | North utility facade | LOC12 | Boundary facade pieces |
| ENV016 | North apartments facade | LOC13 | Boundary apartment pieces |
| ENV017 | General windows, doors and trims | LOC05;LOC06;LOC07;LOC08 | Reusable opening/frame/cornice variants |
| ENV018 | South maintenance stairs | LOC09 | Ascending stair assembly |
| ENV019 | North maintenance stairs | LOC09 | Descending stair assembly |
| ENV020 | Roof walkway and landings | LOC09 | Deck/landing modules |
| ENV021 | Railings and parapets | LOC09;LOC01 | Straight/end/corner safety rail modules |
| ENV022 | Decorative fire escape | LOC07 | Facade fire-escape assembly |
| ENV023 | Alley walls and columns | LOC10 | Narrow masonry/service modules |
| ENV024 | Alley paving and exit lamp | LOC10 | Path marks and light module |
| ENV025 | Checkpoint frame and gate | LOC11 | Static frame plus separate movable gate |
| ENV026 | Checkpoint control panel | LOC11 | Panel with off/on states |
| ENV027 | Checkpoint barriers and sidewall | LOC11 | Barricade/sidewall modules |
| ENV028 | East River entrance arch | LOC02 | Arch and sign assembly |
| ENV029 | North Transit exit arch | LOC14 | Arch/sign/indicator lights |
| ENV030 | Street lamps | LOC03;LOC04 | Pole/arm/lamp reusable pieces |
| ENV031 | Utility poles and cables | LOC03 | Pole/cable spans |
| ENV032 | Dumpsters | LOC03;LOC08 | Prop module |
| ENV033 | Parked/wrecked cars | LOC03 | Vehicle scenery module |
| ENV034 | Crates | LOC03 | Small prop module |
| ENV035 | Hydrants | LOC03 | Street prop |
| ENV036 | Rubble and broken paving | LOC03 | Small dressing/decal kit |
| ENV037 | Puddles and wet surface treatment | LOC03 | Decal/material set |
| ENV038 | Signs and propaganda | LOC05;LOC06;LOC07;LOC08;LOC11 | Diner/laundry/curfew/checkpoint/access/service labels |
| ENV039 | Tower silhouette | LOC15 | Distant landmark layer/mesh per D02 |
| ENV040 | Distant skyline | LOC15 | Background building kit |
| ENV041 | Rain and atmospheric layers | LOC01 | Weather overlays/materials and settings variant |
| ENV042 | Ground contact and shadow treatment | LOC01 | Actor/environment shadow compositing setup |
| ENV043 | Rooftop utility details | LOC09 | Extract existing roof vent/utility modules from source |
| ENV044 | Gate movement presentation | LOC11 | Open/close visual state sequence |
| ENV045 | Family setting modular kit | LOC16 | Expand into one manifest row per approved modular piece and unique landmark; then produce kit |
| ENV046 | Raphael–Karai setting kit | LOC17 | Expand into one manifest row per approved modular piece and unique landmark; then produce kit |
| ENV047 | Baxter-attack setting kit | LOC18 | Expand into one manifest row per approved modular piece and unique landmark; then produce kit |
| ENV048 | Japan last-stand setting kit | LOC19 | Expand into one manifest row per approved modular piece and unique landmark; then produce kit |
| ENV049 | Exile/survival/training setting kits | LOC20 | Expand into one manifest row per approved modular piece and unique landmark; then produce kit |
| ENV050 | Additional occupied-city and ally-story kits | LOC21;LOC22 | Expand into one manifest row per approved modular piece and unique landmark; then produce kit |
| ENV051 | Stronghold/finale/closure kits | LOC23;LOC24 | Expand into one manifest row per approved modular piece and unique landmark; then produce kit |
| ENV052 | Failed-assault setting reuse/kit | LOC25 | Expand into one manifest row per approved modular piece and unique landmark; then produce kit |


## Animation coverage and handoff

Locomotion, interaction and combat require animation synchronized to actual gameplay. The previous production manifest records the following clip requirements/packages. A row is not necessarily one final clip: weapon/era variants, final behavior and rig compatibility are unresolved. Conditional rows remain conditional; this list does not approve new mechanics.

| ID | Actor IDs | Clip / package | Scope | Status |
| --- | --- | --- | --- | --- |
| ANM001 | CHR01 | Idle | BLOCK01 / shared | Blocked: rig/behavior contract missing |
| ANM002 | CHR01 | Walk | BLOCK01 / shared | Blocked: rig/behavior contract missing |
| ANM003 | CHR01 | Run | BLOCK01 / shared | Blocked: rig/behavior contract missing |
| ANM004 | CHR01 | Turn / directional blend | BLOCK01 / shared | Blocked: rig/behavior contract missing |
| ANM005 | CHR01 | Stair ascent | BLOCK01 / shared | Blocked: rig/behavior contract missing |
| ANM006 | CHR01 | Stair descent | BLOCK01 / shared | Blocked: rig/behavior contract missing |
| ANM007 | CHR01 | Dash / recovery | BLOCK01 / shared | Blocked: rig/behavior contract missing |
| ANM008 | CHR01 | Interact / panel use | BLOCK01 / shared | Blocked: rig/behavior contract missing |
| ANM009 | CHR01 | Light attack 01 | BLOCK01 / shared | Blocked: rig/behavior contract missing |
| ANM010 | CHR01 | Hit reaction | BLOCK01 / shared | Blocked: rig/behavior contract missing |
| ANM011 | CHR01 | Defeat | BLOCK01 / shared | Blocked: rig/behavior contract missing |
| ANM012 | CHR01 | Guard / counter response | BLOCK01 / shared | Blocked: rig/behavior contract missing |
| ANM013 | CHR01 | Light attack 02 | Shared; adoption D07 | Conditional: scope approval required |
| ANM014 | CHR01 | Light attack 03 | Shared; adoption D07 | Conditional: scope approval required |
| ANM015 | CHR01 | Heavy attack | Shared; adoption D07 | Conditional: scope approval required |
| ANM016 | CHR01 | Guard break / stagger | Shared; adoption D07 | Conditional: scope approval required |
| ANM017 | CHR01 | Healing / cache use | Shared; adoption D07 | Conditional: scope approval required |
| ANM018 | CHR01 | Weapon draw / holster / switch | Shared; adoption D07 | Conditional: scope approval required |
| ANM019 | CHR03 | Idle / patrol | Acts/encounters D04/D06 | Blocked: rig/behavior contract missing |
| ANM020 | CHR03 | Locomotion / turn | Acts/encounters D04/D06 | Blocked: rig/behavior contract missing |
| ANM021 | CHR03 | Attack anticipation / strike / recovery | Acts/encounters D04/D06 | Blocked: rig/behavior contract missing |
| ANM022 | CHR03 | Hit / stagger | Acts/encounters D04/D06 | Blocked: rig/behavior contract missing |
| ANM023 | CHR03 | Defeat / disable | Acts/encounters D04/D06 | Blocked: rig/behavior contract missing |
| ANM024 | CHR04 | Idle / patrol | Acts/encounters D04/D06 | Blocked: rig/behavior contract missing |
| ANM025 | CHR04 | Locomotion / turn | Acts/encounters D04/D06 | Blocked: rig/behavior contract missing |
| ANM026 | CHR04 | Attack anticipation / strike / recovery | Acts/encounters D04/D06 | Blocked: rig/behavior contract missing |
| ANM027 | CHR04 | Hit / stagger | Acts/encounters D04/D06 | Blocked: rig/behavior contract missing |
| ANM028 | CHR04 | Defeat / disable | Acts/encounters D04/D06 | Blocked: rig/behavior contract missing |
| ANM029 | CHR05 | Idle / patrol | Acts/encounters D04/D06 | Blocked: rig/behavior contract missing |
| ANM030 | CHR05 | Locomotion / turn | Acts/encounters D04/D06 | Blocked: rig/behavior contract missing |
| ANM031 | CHR05 | Attack anticipation / strike / recovery | Acts/encounters D04/D06 | Blocked: rig/behavior contract missing |
| ANM032 | CHR05 | Hit / stagger | Acts/encounters D04/D06 | Blocked: rig/behavior contract missing |
| ANM033 | CHR05 | Defeat / disable | Acts/encounters D04/D06 | Blocked: rig/behavior contract missing |
| ANM034 | CHR07 | Idle / hover / mechanical loop | Act/encounter assignment TBD | Conditional: scope approval required |
| ANM035 | CHR07 | Movement and turn | Act/encounter assignment TBD | Conditional: scope approval required |
| ANM036 | CHR07 | Attack sequence if combat role approved | Act/encounter assignment TBD | Conditional: scope approval required |
| ANM037 | CHR07 | Damage / disabled state if approved | Act/encounter assignment TBD | Conditional: scope approval required |
| ANM038 | CHR08 | Idle / hover / mechanical loop | Act/encounter assignment TBD | Conditional: scope approval required |
| ANM039 | CHR08 | Movement and turn | Act/encounter assignment TBD | Conditional: scope approval required |
| ANM040 | CHR08 | Attack sequence if combat role approved | Act/encounter assignment TBD | Conditional: scope approval required |
| ANM041 | CHR08 | Damage / disabled state if approved | Act/encounter assignment TBD | Conditional: scope approval required |
| ANM042 | CHR09 | Idle / hover / mechanical loop | Act/encounter assignment TBD | Conditional: scope approval required |
| ANM043 | CHR09 | Movement and turn | Act/encounter assignment TBD | Conditional: scope approval required |
| ANM044 | CHR09 | Attack sequence if combat role approved | Act/encounter assignment TBD | Conditional: scope approval required |
| ANM045 | CHR09 | Damage / disabled state if approved | Act/encounter assignment TBD | Conditional: scope approval required |
| ANM046 | CHR02 | Locomotion and combat stance | V | Conditional: scope approval required |
| ANM047 | CHR02 | Approved attack set and recoveries | V | Conditional: scope approval required |
| ANM048 | CHR02 | Hit/reaction and phase transitions | V | Conditional: scope approval required |
| ANM049 | CHR02 | Final confrontation performance | V | Conditional: scope approval required |
| ANM050 | CHR06 | Idle and locomotion if needed | IV / appearances TBD | Conditional: scope approval required |
| ANM051 | CHR06 | Dialogue gestures and scene performance | IV / appearances TBD | Conditional: scope approval required |
| ANM052 | CHR10 | Idle and locomotion if needed | IV / appearances TBD | Conditional: scope approval required |
| ANM053 | CHR10 | Dialogue gestures and scene performance | IV / appearances TBD | Conditional: scope approval required |
| ANM054 | CHR01 | Act-specific movement / combat / narrative clip expansion | I/III era variants | Conditional: scope approval required |
| ANM055 | CHR11 | Act-specific movement / combat / narrative clip expansion | I/II | Conditional: scope approval required |
| ANM056 | CHR12 | Act-specific movement / combat / narrative clip expansion | I/II | Conditional: scope approval required |
| ANM057 | CHR13 | Act-specific movement / combat / narrative clip expansion | I/II | Conditional: scope approval required |
| ANM058 | CHR14 | Act-specific movement / combat / narrative clip expansion | II | Conditional: scope approval required |
| ANM059 | CHR15 | Act-specific movement / combat / narrative clip expansion | II | Conditional: scope approval required |
| ANM060 | CHR16;CHR17;CHR18 | Appearance and animation scope resolution | Campaign | Conditional: scope approval required |


For each completed clip record actor and rig version, duration, looping, root-motion/in-place policy, animation-event timing, allowed transitions and cancellation, weapon sockets and a preview at the fixed gameplay camera. Exact clip timings and root-motion policy are TBD. Source motion must be adapted and verified on the actual rig; do not equate downloading a motion with finishing an animation.

## Art acceptance

1. Assemble a representative final 2D environment section with a real 3D character under the same fixed camera.
2. Verify character size, ground contact, front/behind ordering, roof elevation, facade occlusion and absence of visible seams.
3. Compare the composite with approved style/reference selection at actual desktop and phone gameplay sizes.
4. Verify that replacing art preserves all three BLOCK01 routes and gate behavior.
5. Check all relevant character poses for shell, cloth, hand and weapon intersections; confirm readable silhouettes.
6. Record missing assets rather than substituting new designs. Keep prototype and final exports clearly distinguished.

Performance budgets, final reference selections, exact camera preset, audio/VFX scope and final UI typography remain TBD. The current blockout's palette and fonts are not automatically a locked design system.

## Related documents

[GAME_BIBLE.md](GAME_BIBLE.md) defines cast/story authority. [ACTS_AND_MAPS.md](ACTS_AND_MAPS.md) assigns kits to story locations. [GAMEPLAY_SYSTEMS.md](GAMEPLAY_SYSTEMS.md) defines collision, events, input and actor adapters.
