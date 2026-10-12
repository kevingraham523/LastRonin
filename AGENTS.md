# Shared production rules

Read `README.md`, `docs/GAME_BIBLE.md`, `docs/ART_BIBLE.md`, `docs/PRODUCTION_BOARD.md`, and the manifests before beginning an assigned task. Inspect the current worktree, branch, and working changes. These rules organize work; they do not authorize new features, deleting systems, or publishing anything.

## Preserve the reference work

- Baseline commit: `4cff68e827cc5edc98a6383858fae2fe7964c76d`. Its 664 files remain at their original paths. Do not delete, relocate, rebuild, or bulk-format them as part of routine setup or integration.
- The existing root Blender libraries, root guides/reports/previews, `scripts/`, `assets/Creature Pack/`, and `qa*` paths are reference material. All roles read them; changing any of them requires that exact scope in the assigned task. Prefer a derived working copy in the owning role's directory, preserving the existing mesh, rig, actions, and texture.
- `scripts/*.py` are historical, order-dependent scripts. Many embed the absolute original workspace path and save over root `.blend` files. Running one from a different worktree can still modify the original checkout. Do not run them against the shared checkout. Adapt the required operation into the role's `tools/blender/` subdirectory with explicit worktree-relative inputs/outputs first.
- Never treat the presence of a historical experiment or older QA result as approval to replace the current library. `Ronin_Animation_Library_QA_Report.txt` is the current animation QA reference.
- Keep Mutant Walking excluded. Keep the corrected step recovery, narrower run arms, and existing Sad Walk unless the user explicitly changes that direction.
- Do not run destructive Git cleanup, discard someone else's edits, or resolve a binary conflict by blindly accepting one side.

## Exclusive ownership

Each task has one named owner/role and one branch/worktree. The most specific path rule wins. Unlisted new paths belong to the integration role until assigned. Existing baseline paths remain protected by the rule above, regardless of their historical domain.

| Role | Files this role may author in its assigned task | Boundaries |
| --- | --- | --- |
| Animation | `assets/characters/**`, `tools/blender/animation/**`, `docs/workstreams/animation/**` | Rig, animation, character exports and previews. Do not edit environment files, gameplay code, or shared manifests. |
| Environment | `assets/environments/**`, `tools/blender/environment/**`, `godot/environments/**`, `docs/workstreams/environment/**` | Environment sources, exported meshes, and self-contained environment scenes. Do not edit the character rig, player controller, project settings, or main scene. |
| Gameplay | `prototype/**`, `godot/**` except `godot/environments/**`, `godot/characters/**`, and `godot/README.md`; `docs/workstreams/gameplay/**` | Engine bootstrap, input, player/camera/controller, animation state machine, main-scene assembly, tests. Reference accepted art; do not edit source art. |
| Integration / production lead | Root `AGENTS.md`, `README.md`, `.gitignore`, `.gitattributes`; `docs/**` except role workstreams; `tools/blender/README.md`, `tools/blender/inspect_library.py`; `godot/README.md`, `godot/characters/**` | Shared specifications, board/manifests, approved character staging, and merge coordination. Does not silently author changes in another role's files. |

The initial setup creates documentation/placeholders in these areas. After that setup commit, the table controls task ownership. No `.github/CODEOWNERS` or branch protection is configured: these are explicit collaboration rules, not Git-enforced locks.

## Branch and worktree workflow

1. The production lead assigns a board ID, owner, acceptance criteria, allowed paths, and a base commit. One active writer per asset or subsystem, including within a role.
2. Use a separate branch and worktree for each concurrent task: `codex/animation/<task>`, `codex/environment/<task>`, `codex/gameplay/<task>`. Do not share a working directory or run Blender saves into a sibling worktree.
3. Start all task branches from the same reviewed integration revision. The setup branch is initially `codex/production-setup`; use `main` after this setup is merged there. Do not start from an arbitrary agent's unfinished branch.
4. If Codex managed worktree tools are available, prefer them. Equivalent manual commands, from the repository root, are:

   ```sh
   git worktree list
   git worktree add -b codex/animation/export-pass ../last-ronin-animation codex/production-setup
   git worktree add -b codex/environment/test-room ../last-ronin-environment codex/production-setup
   git worktree add -b codex/gameplay/bootstrap ../last-ronin-gameplay codex/production-setup
   ```

   These are examples for future assigned work, not worktrees created by the setup. Existing branches/paths must be inspected and reused only if suitable; do not reset them. Worktrees share Git history but have independent working files.
5. Resolve paths from the current worktree. New Blender tools must require explicit input/output paths and refuse accidental output outside that worktree. New previews and QA outputs belong beside the task's owned assets, not in historical `qa*` directories.
6. Commit only the assigned paths. Before handoff, inspect `git diff --name-status <base>...HEAD` and `git status --short`. Keep unrelated user edits out of the commit. Do not merge another role's branch from your worktree.
7. Publish a handoff in the role's `docs/workstreams/<role>/HANDOFF.md`: board ID, branch/base/head, changed paths, exact reproduction commands, asset IDs/action names, QA evidence, proposed manifest rows, and remaining limits. Never mark shared work complete yourself by editing another owner's board/manifest.
8. The lead verifies ownership, reviews evidence, and integrates each focused commit. The lead then updates shared manifests/board and runs cross-system validation. Commit the reviewed engine-ready character export under `godot/characters/`; gameplay references it rather than re-exporting or modifying it.

## Cross-role contracts and conflicts

- Source art is editable only by its owning role. Deliver runtime candidates under that role's source asset tree first. Exported candidates must include scale/axes, action names/ranges, root-motion choice, skeleton/weight handling, and QA notes. Engine staging is a distinct reviewed step.
- The planned Godot project root is `godot/`; a file outside that directory is not a `res://` asset. Gameplay references character deliveries under `res://characters/` and environments under `res://environments/`. These paths are reserved contracts, not implemented scenes.
- Shared manifest IDs and existing action/bone names are stable interfaces. Propose changes in your handoff; the lead updates shared files once after reconciliation.
- If work requires another owner's file, record a scoped handoff/dependency and continue independent work. Get reassignment from the lead rather than editing across the boundary. A user instruction explicitly assigning that scope takes precedence.
- Binary `.blend`, `.fbx`, and `.glb` files are not text-mergeable. Assign one writer, preserve both conflicting versions, and let the owning role reconcile in Blender with fresh QA. Do not concatenate files, blindly choose “ours/theirs,” or rebuild from scratch.
- No mass asset migration, history rewrite, LFS migration, engine upgrade, source rebuild, or deletion as a side effect of a feature task. Those require a separate assigned change with preservation checks.

## Completion evidence

Animation: relevant pose/playback review, foot contact, knee direction, seams, loops/turn endpoints, preserved source geometry/actions, and export limitations. Environment: scale/origin, collision and traversal checks, material dependencies, and a scene that runs without changing gameplay files. Gameplay: engine version, exact run command, input mapping, reproducible smoke test, and fallback behavior if art is unavailable. Integration: confirm deliverables exist in a fresh worktree, shared paths resolve, and actual game startup works before claiming a runnable game.

Do not claim a placeholder directory is a working system or report historical QA as a new engine test. Document untested behavior and dependencies precisely.
