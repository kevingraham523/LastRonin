# Production board

Updated 12 October 2026. This board covers **all five arcs**, the first complete block (M1), shared systems and migration. It is not a claim that 13 chapters or any additional mission count has been approved. MIS rows are recovered beat packages, not chapter counts.

Role codes: **I** integration/production lead; **G** gameplay; **A** animation/characters; **E** environments/2D art; **Q** QA; **K** Kevin for creative decisions. Owners are roles, not staffed individuals. Assign a named writer and allowed paths before concurrent work. No dates or estimates are invented; D13 controls capacity/scheduling.

Statuses: DONE = acceptance evidence exists for stated scope; READY = can begin; WAIT = depends on listed work/input; CONDITIONAL = requires a scope decision before production. P0 unblocks foundations/M1; P1 builds approved gameplay/content; P2 expands content or release coverage after dependencies. Priority is production order, not story importance. `Dxx` dependencies refer to the Game Bible decision register. Other dependency tokens are task IDs in this board. No blank dependency implies permission to invent missing content.

## Foundation and immediate sequence

| ID | Priority | Owner | Status | Deliverable / acceptance | Depends on |
| --- | --- | --- | --- | --- | --- |
| DOC-01 | P0 | I | DONE | Production docs/manifests; test page removed; source hashes and scoped checks recorded; dedicated setup commit | — |
| P0-01 | P0 | I | READY | Intake/storage plan, then separately copy approved B1/G3/animation sources with hashes; clean-clone retrieval works; originals retained | — |
| P0-02 | P0 | G/I | READY | D05 decision: pin Godot build/renderer/templates, browser/export targets and parity baseline; preserve B1; G3 is older reference | D05 |
| P0-04 | P0 | A/K | READY | D03/D08 character source/era mapping; confirm CHR01 candidate, inventory other models; retain rest pose and source library | D03;D08 |
| P0-05 | P0 | G/A/K | READY | D04/D07 M1 encounter/story/weapon brief, controls, combat timing, root-motion policy and failure/retry contract | D04;D07 |
| P0-06 | P0 | G/E/K | READY | D09 real desktop/phone device matrix and numeric frame-time/load/memory/texture budgets | D09 |
| A-01 | P0 | A | WAIT | Bake/export candidate rig + locomotion/idle; skeleton/weight/root/texture comparison passes; no source changes | P0-01;P0-02;P0-04 |
| P0-07 | P0 | G/I | WAIT | Select browser skinning/import approach; real model loads through replaceable wrapper in browser and Godot; retain working baseline | P0-02;A-01 |
| P0-03 | P0 | E/G/K | WAIT | D02 camera/depth/pixel-scale contract demonstrated with real actor, facade, roof/stairs and foreground; fixed orientation accepted | P0-07;P0-06;D02 |
| P1-01 | P1 | I/K | READY | D01/D06/D12 chronology and scene/map briefs; use stable arc IDs until approved | D01;D06;D12 |
| P1-02 | P1 | I/E/G/K | READY | D10/D14 exact references, audio/subtitle/scene-skip scope and approved source list | D10;D14 |
| P1-03 | P1 | G/A/K | CONDITIONAL | Resolve D11 extras; explicitly include or omit jump/climb/vault/stealth/takedowns before production | D11 |
| A-02 | P0 | A | WAIT | M1 clips ANM005–012 and any approved weapon variants; events/transitions/grips, feet and shell/cloak QA | A-01;P0-05 |
| A-03 | P1 | A | WAIT | Approved M1 enemy model/rig/clip subset; each selected CHR/EN mapping and ready/attack/hit/defeat delivery tested | P0-04;P0-05 |
| A-04 | P1 | A | WAIT | Retained optional combat/era/actor clip packages; split ANM requirement packages into versioned concrete clips | P0-05;P1-01;P1-03 |
| E-01 | P0 | E | WAIT | Representative final modular 2D kit and real-character composite; exact pivot/depth/collision contract | P0-03;A-01 |
| E-02 | P1 | E | WAIT | BLOCK01 ENV001–044 final kit; preserve three routes and gate; every family has module/state metadata or justified not-needed decision | E-01;P0-05 |
| E-03 | P1 | E/I | WAIT | Break ENV045–052 into approved per-map piece lists, quantities and dependencies; conditional prologue stays conditional | P1-01;E-01 |

READY decision tasks need their listed decision resolved as the deliverable; they do not require an invented answer to start collecting evidence. First practical sequence: source intake/version selection and M1 brief → character export and browser import spike → camera/composite → integrated browser block → Godot parity. Arc briefs can progress independently.

## Shared systems: complete scope from GAMEPLAY_SYSTEMS

| ID | Priority | Owner | Status | Deliverable / acceptance | Depends on |
| --- | --- | --- | --- | --- | --- |
| G-SYS01 | P0 | G | WAIT | Motor adapter preserves normalized movement, grounded stairs/roof and obstacle-safe dash | P0-01;P0-05 |
| G-SYS02 | P0 | G | WAIT | Fixed camera/follow/cutaway; no release rotation; routes and actors readable | P0-03 |
| G-SYS03 | P0 | G/E | WAIT | Collision categories, surface IDs, gate links and height-aware navigation; no wrong-floor paths/hits | G-SYS01;E-01 |
| G-SYS04 | P0 | G | WAIT | Unified keyboard/touch action map, modal/blur/pointer reset; resolve E/Q/R/Shift conflicts | P0-05 |
| G-SYS05 | P0 | G/E | WAIT | Validated interactions, gate art/collision/nav sync, idempotent use; bypass routes independent | G-SYS03;G-SYS04 |
| G-SYS06 | P0 | G | WAIT | Approved directional attacks: startup/active/recovery, once-per-target hit and wall/floor obstruction | P0-05;A-02;G-SYS03 |
| G-SYS07 | P1 | G | WAIT | Approved guard/counter/reaction rules; facing and interrupt cases tested | G-SYS06 |
| G-SYS08 | P0 | G | WAIT | Approved dash/resource/cancel policy; no tunneling or unintended immunity | G-SYS01;P0-05 |
| G-SYS09 | P0 | G | WAIT | Enemy/encounter lifecycle, stable spawns, clear/fail/reset and pathing | G-SYS06;A-03;G-SYS03 |
| G-SYS10 | P0 | G | WAIT | Health, defeat and checkpoint retry; no post-death actions or duplicated actors/rewards | G-SYS09;G-SYS13 |
| G-SYS11 | P1 | G | CONDITIONAL | If D07 retains healing/caches, validate capacity, once-only use and save/retry; otherwise record exclusion | P0-05;G-SYS13 |
| G-SYS12 | P0 | G | WAIT | Mission IDs and prerequisites, optional vs mandatory flags, once-only completion | P0-05;G-SYS05 |
| G-SYS13 | P0 | G | WAIT | Versioned campaign/checkpoint storage separate from settings; corrupt/denied/version tests | G-SYS12 |
| G-SYS14 | P1 | G | WAIT | Narrative scene sequencing, subtitles, skip/outcome idempotence and control restoration | P1-01;P1-02;G-SYS12 |
| G-SYS15 | P1 | G/A | WAIT | AI brothers follow/regroup/teamwork without blocking objectives; roles match approved brief | FAM-01;G-SYS03;G-SYS09 |
| G-SYS16 | P1 | G/A | WAIT | Approved weapon mastery/unlock data; earned progression survives retry/load | LOST-01;G-SYS06;G-SYS13 |
| G-SYS17 | P1 | G | WAIT | Map/spawn transitions and chronology graph; flashback and present state isolated | P1-01;G-SYS13 |
| G-SYS18 | P1 | G | WAIT | HUD/objective/map feedback readable on desktop/phone; touch controls avoid key cues | G-SYS04;G-SYS06;G-SYS12 |
| G-SYS19 | P1 | G | WAIT | Approved audio/VFX cue events, gesture start, mute persistence and warning readability | P1-02;G-SYS06 |
| G-SYS20 | P0 | G | WAIT | Preserve settings/pause/failure diagnostics; invalid data and unsupported features recover safely | P0-01;G-SYS04 |
| G-SYS21 | P0 | G/I | WAIT | Model/animation wrapper, clip alias/socket/event adapter; real-model swap requires no controller rewrite | P0-07;A-02 |
| G-SYS22 | P0 | G/E | WAIT | Hybrid compositing/loading/budgets on named devices; measure alpha/shadow/skin performance | E-01;P0-06;G-SYS21 |
| G-SYS23 | P1 | G/I/Q | WAIT | Godot port of accepted M1 behavior; fresh-clone import/run/export and route/combat/save parity | M1-04;P0-02 |
| G-SYS24 | P1 | G | WAIT | Approved Hiroto behavior and ending completion/resume states; no unreachable phases or reload trap | FINAL-01;G-SYS09;G-SYS14;G-SYS17 |

No row above is marked implemented merely because B1 or G3 has a reference component. Before delivery, split shared-owner rows into exclusive path assignments with a single accountable owner.

## Enemy coverage

| ID | Priority | Owner | Status | Deliverable / acceptance | Depends on |
| --- | --- | --- | --- | --- | --- |
| G-EN01 | P1 | G/A | WAIT | CHR03 Standard Synja: approved perception/attack/recovery/defeat, complete clip set and reset | P0-05;A-03;G-SYS09 |
| G-EN02 | P1 | G/A | WAIT | CHR04 Foot Bot: approved distinct behavior and purple-accent asset mapping | P0-05;P0-04;G-SYS09 |
| G-EN03 | P1 | G/A | WAIT | CHR05 Elite Synja: approved distinction and white/red asset mapping | P0-05;P0-04;G-SYS09 |
| G-EN04 | P1 | G/A | WAIT | CHR08 Large Mouser: approve articulation/combat scale and role before implementation | P0-04;P1-01;G-SYS09 |
| G-EN05 | P1 | G/A | WAIT | CHR09 Flying Mouser: approved flight, height, detection and attack rules | P0-04;P1-01;G-SYS09 |
| G-EN06 | P2 | G/A | CONDITIONAL | CHR07 patrol vehicle atmosphere; combat only if separately approved; no automatic fightable vehicle | P0-04;P1-01 |
| G-EN07 | P1 | G/A | WAIT | CHR02 Hiroto: approved final encounter, phases/animations and outcome contract | FINAL-01;G-SYS24 |
| G-EN08 | P1 | G/A | CONDITIONAL | CHR15 Karai confrontation: playable combat role only if approved; otherwise authored scene scope | FALL-01;G-SYS09 |
| G-EN09 | P1 | G/A | WAIT | Baxter attack forces: approved roster; CHR16 need not be an on-screen/fightable boss | FALL-01;G-SYS09 |

LEG01–04 remain reference descriptions; retrieve and evaluate legacy source if useful. Do not silently map Gatekeeper to Hiroto/Mouser, or a legacy drone/shield unit to a roster actor.

## M1: first complete playable city block

| ID | Priority | Owner | Status | Deliverable / acceptance | Depends on |
| --- | --- | --- | --- | --- | --- |
| M1-01 | P0 | G/E/A | WAIT | B1 routes with real Ronin, final modular kit and approved camera; model replacement preserves motor/geometry | E-02;G-SYS01;G-SYS02;G-SYS05;G-SYS21 |
| M1-02 | P0 | G/A | WAIT | Approved encounter and combat subset; includes required guard/resource/healing choices explicitly | P0-05;G-SYS06;G-SYS07;G-SYS08;G-SYS09;G-SYS10 |
| M1-03 | P0 | G/I | WAIT | MIS01 authored objective/exit and MIS02 approved optional memory; retry/save/story flags and usable HUD | G-SYS12;G-SYS13;G-SYS14;G-SYS18;P1-01 |
| M1-04 | P0 | Q/I | WAIT | Browser segment acceptance: three routes, encounter/reset, story/exit, input, models and device performance; publish evidence | M1-01;M1-02;M1-03;G-SYS19;G-SYS20;G-SYS22 |

## FAMILY (earlier Act I): LOC16, MIS03–04, ENV045

| ID | Priority | Owner | Status | Deliverable / acceptance | Depends on |
| --- | --- | --- | --- | --- | --- |
| FAM-01 | P1 | I/K | WAIT | Named setting/map graph, controlled character/era, training/team objectives, dialogue and brother roles; no assumed sewer lair | P1-01;D06;D08 |
| FAM-02 | P1 | E/A | WAIT | ENV045 pieces and family-era CHR01/11/12/13; Splinter only for specified scenes; ANM054–057 expansion | FAM-01;E-03;A-01 |
| FAM-03 | P1 | G | WAIT | MIS03 training and MIS04 teamwork with AI brothers and authored scenes | FAM-02;G-SYS15;G-SYS14;G-SYS17 |
| FAM-04 | P1 | Q/I | WAIT | Every approved FAMILY objective/scene, companion recovery, retry, exit and flashback save isolation passes | FAM-03 |

## FALL (earlier Act II): LOC17–19, MIS05–07, ENV046–048

| ID | Priority | Owner | Status | Deliverable / acceptance | Depends on |
| --- | --- | --- | --- | --- | --- |
| FALL-01 | P1 | I/K | WAIT | Three separate loss briefs: actor control, exact locations, encounter roster, scripted outcome vs player failure, dialogue/order | P1-01;D06;D08;D12 |
| FALL-02 | P1 | E/A/G | WAIT | MIS05 Raphael–Karai at LOC17; ENV046 and CHR11/15 scene/clip scope; no unapproved boss phases | FALL-01;E-03;A-04;G-SYS14;G-SYS17 |
| FALL-03 | P1 | E/A/G | WAIT | MIS06 Baxter attack/Leonardo sacrifice at LOC18; ENV047, CHR12 and approved forces | FALL-01;E-03;A-04;G-EN09;G-SYS14;G-SYS17 |
| FALL-04 | P1 | E/A/G | WAIT | MIS07 Donatello/Splinter Japan last stand at LOC19; ENV048, CHR13/14 and authored outcome | FALL-01;E-03;A-04;G-SYS14;G-SYS17 |
| FALL-05 | P1 | Q/I | WAIT | All three loss packages, skip/retry distinctions and context transitions verified; source-era state never leaks | FALL-02;FALL-03;FALL-04 |

## LOST (earlier Act III): LOC20, MIS08–10, ENV049

| ID | Priority | Owner | Status | Deliverable / acceptance | Depends on |
| --- | --- | --- | --- | --- | --- |
| LOST-01 | P1 | I/K | WAIT | Ordered journey/map briefs and approved mastery challenges, weapons/unlock order and narrative beats; no invented survival economy | P1-01;P0-05;D06;D08 |
| LOST-02 | P1 | E/A | WAIT | Per-location ENV049 kits, Ronin era variants and approved four-weapon/scene clip expansion | LOST-01;E-03;A-04 |
| LOST-03 | P1 | G | WAIT | MIS08 exile/survival, MIS09 mastery, MIS10 grief/journey and return handoff; only specified locations/challenges | LOST-02;G-SYS16;G-SYS14;G-SYS17 |
| LOST-04 | P1 | Q/I | WAIT | All approved journey edges/objectives and unlock/save/retry cases pass, no duplicate/unearned mastery | LOST-03 |

## RETURN (earlier Act IV): LOC21–22 plus BLOCK01, MIS11–13, ENV001–044/050

| ID | Priority | Owner | Status | Deliverable / acceptance | Depends on |
| --- | --- | --- | --- | --- | --- |
| RETURN-01 | P1 | I/K | WAIT | District/connection and ally-story briefs; BLOCK01 placement, April/Casey/Resistance roles and optional-content policy | P1-01;D06;D08 |
| RETURN-02 | P1 | E/A | WAIT | ENV050 extensions, CHR06/10/17 era/mapping, selected opposition and scene clips; no assumed hub or playable Casey | RETURN-01;E-03;A-04 |
| RETURN-03 | P1 | G | WAIT | MIS11 city/Synja combat, MIS12 ally/Resistance story, MIS13 approved optional exploration; connect M1 as approved | RETURN-02;M1-04;G-SYS14;G-SYS17;G-EN01 |
| RETURN-04 | P1 | Q/I | WAIT | Every approved district, ally scene, optional flag, checkpoint and transition passes | RETURN-03 |

## FINAL (earlier Act V): LOC23–24, MIS14–17, ENV051

| ID | Priority | Owner | Status | Deliverable / acceptance | Depends on |
| --- | --- | --- | --- | --- | --- |
| FINAL-01 | P1 | I/K | WAIT | Stronghold graph/approach, escalation encounters, Hiroto phases, arena, exact outcome/closure and post-completion resume policy | P1-01;D06;D12 |
| FINAL-02 | P1 | E/A | WAIT | ENV051 modules and CHR02 final rig/ANM046–049; required other cast from approved staging | FINAL-01;E-03;A-04 |
| FINAL-03 | P1 | G | WAIT | MIS14 infiltration and MIS15 escalation through authored stronghold graph | FINAL-02;G-SYS09;G-SYS17 |
| FINAL-04 | P1 | G/A | WAIT | MIS16 confrontation and MIS17 closure with once-only outcome and valid resume | FINAL-03;G-EN07;G-SYS14;G-SYS24 |
| FINAL-05 | P1 | Q/I | WAIT | All approved phases, defeat/retry, scene skip, closure and reload after completion pass | FINAL-04 |

## Conditional opening and release

| ID | Priority | Owner | Status | Deliverable / acceptance | Depends on |
| --- | --- | --- | --- | --- | --- |
| PRO-01 | P1 | I/K | CONDITIONAL | Decide MIS18/LOC25 failed-assault opening, reuse/ENV052, failure/rescue and flashback handoff; do not invent a sixth act | P1-01;D01;D12 |
| PRO-02 | P1 | E/A/G/Q | CONDITIONAL | Produce and test only the approved opening package; explicitly record exclusion if not retained | PRO-01;E-03;G-SYS14;G-SYS17 |
| CAM-01 | P2 | I/Q | WAIT | Whole-campaign coverage matrix: every approved map/MIS/actor/clip/transition assigned and tested; no omitted act | FAM-04;FALL-05;LOST-04;RETURN-04;FINAL-05;PRO-01 |
| REL-01 | P2 | I/G/Q | WAIT | Godot release candidate, reproducible clean-clone build/export, device/accessibility/performance and complete save migration checks | CAM-01;G-SYS23;P0-06;P1-02 |

CAM-01/REL-01 additionally require PRO-02 only if the opening is retained, G-SYS11 if healing/caches are retained, and all roster enemies/ANM packages assigned by approved content briefs. Do not close a conditional dependency by silently omitting approved content. All-act detailed piece/scene counts are blocked by D06, not estimated as zero.

## Current findings to carry into assigned work

- B1 is available outside Git: traversal/source syntax checked; browser routes were not freshly played in this setup.
- G0 has a confirmed parser error; G3 is the corrected older blockout and passed a limited headless smoke check. Neither is a completed port.
- A1 has a real model/rig and corrected clips; no accepted engine export, events, sockets or transition graph. Keep Mutant Walking excluded.
- Current 2D exports, legacy combat source, complete map/scripts and most model-to-roster mappings are not verified. Manifests expose these gaps without replacing assets.
- Document setup is complete only for planning/inventory. No content, rendering, combat or migration task is made DONE by this commit.
