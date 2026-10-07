# Vileterra — Codex Instructions

## 1. Project

Project: Vileterra

Vileterra is a Minecraft MMORPG server built with Minestom 26.2.

Primary technology:

* Java
* Minestom 26.2
* Gradle
* PostgreSQL

The GitHub repository containing the project documentation is:

Vileterra/ProjectVClosed

The main roadmap is stored in:

README.md

---

# 2. Core execution rule

WORK ON EXACTLY ONE ROADMAP ITEM AT A TIME.

This is the most important rule in this file.

Never implement multiple roadmap items in one task just because they are related.

For every task:

1. Identify exactly one roadmap item.
2. Read only the information relevant to that item.
3. Inspect the existing code relevant to that item.
4. Determine what is already implemented.
5. Implement only the selected roadmap item.
6. Integrate it with the existing project.
7. Build and test the project.
8. Fix problems caused by the implementation.
9. Verify that the roadmap item is actually complete.
10. Stop.

Do NOT automatically continue to the next roadmap item.

The next roadmap item must be handled by a new task/turn.

---

# 3. Context and token efficiency

Do NOT read the entire repository unnecessarily.

Do NOT reread every documentation file before every task.

Do NOT repeatedly load the entire README.md if only one roadmap item is being implemented.

Use targeted reading.

When working on a roadmap item:

1. Read the relevant roadmap section.
2. Identify the systems affected by that item.
3. Inspect only the relevant source files.
4. Inspect additional files only when necessary.

Avoid loading unrelated systems into context.

The goal is to minimize unnecessary context usage while maintaining correctness.

---

# 4. Roadmap is the source of planned work

README.md contains the current project roadmap.

Treat the roadmap as the planned feature specification.

However, the existing source code is the source of truth for what actually exists.

Never assume that a roadmap item is unimplemented simply because the README says so.

Before implementing an item, inspect the existing implementation.

A roadmap item may be:

* not implemented
* partially implemented
* fully implemented
* implemented incorrectly
* implemented using an outdated approach
* implemented but no longer compatible with the current architecture

Determine its actual state from the code.

---

# 5. Existing implementation audit

Before implementing a roadmap item, compare the requested functionality against the existing code.

If functionality already exists:

* reuse it when appropriate
* improve it when necessary
* remove obsolete implementations when necessary
* avoid creating duplicate systems

Do not create a second implementation of a system that already exists.

If the existing implementation conflicts with the roadmap or current architecture, refactor it instead of blindly adding another system.

---

# 6. Do not implement future roadmap items

While implementing roadmap item N:

DO NOT implement N+1, N+2, or unrelated future features.

Even if you notice that a future feature would be easy to implement, do not implement it yet.

You may prepare clean extension points when genuinely necessary, but do not implement future functionality prematurely.

---

# 7. Handling dependencies between roadmap items

Sometimes the selected roadmap item depends on functionality that belongs to a later roadmap item.

In that situation:

1. Determine whether the dependency is actually required.
2. Implement the smallest necessary foundation.
3. Do not implement the full future feature.
4. Clearly document what was prepared.
5. Continue only with the selected roadmap item.

Do not use dependencies as an excuse to implement several roadmap items at once.

---

# 8. Code quality

Prefer the existing project architecture when it is sound.

Do not perform large unrelated refactors.

Do not rename or reorganize large parts of the project without a concrete reason.

Do not introduce duplicate managers, services, repositories, event systems, or database layers.

Do not invent Minestom APIs.

Always verify APIs against the actual Minestom 26.2 dependency used by the project.

If an API does not exist, find the correct API rather than creating a fake abstraction to hide the problem.

---

# 9. Build and verification

After implementing a roadmap item:

1. Run the appropriate Gradle build.
2. Run relevant tests if they exist.
3. Check compilation errors.
4. Check runtime-relevant errors when possible.
5. Fix problems caused by the implementation.

Do not mark a roadmap item as complete if the project does not compile.

Do not leave known compilation errors unresolved.

Do not leave fake implementations, empty methods, or placeholder TODO implementations unless the roadmap item explicitly requires a placeholder.

---

# 10. Roadmap completion

A roadmap item may be considered complete only when:

* the required functionality is implemented
* it is integrated into the existing architecture
* existing functionality still works
* the project builds successfully
* relevant tests/checks pass
* there is no obvious duplicate implementation
* the implementation matches the intended roadmap behavior

Do not mark an item complete merely because some code was written.

---

# 11. Progress tracking

The roadmap itself may be stored in README.md.

When the project workflow provides a dedicated roadmap-state file, use it to record progress.

If no roadmap-state file exists, do not create unnecessary documentation files unless the task explicitly requires them.

When a roadmap item is completed, clearly record its completion in the designated project state/location.

Do not mark future items as complete.

---

# 12. Git and changes

Keep changes focused on the current roadmap item.

Do not modify unrelated files without a reason.

Before making large changes, inspect the current implementation.

Preserve existing working functionality.

If the current task requires removing obsolete code, remove it rather than leaving duplicate dead systems behind.

---

# 13. When starting a new task

At the beginning of every new task:

1. Determine the repository and current project state.
2. Read this AGENTS.md.
3. Locate the current roadmap in README.md.
4. Identify the specific roadmap item requested by the user.
5. Read only the relevant roadmap section.
6. Inspect the relevant existing code.
7. Implement exactly that item.

If the user explicitly asks to "continue the roadmap", find the first genuinely incomplete roadmap item based on the current code and documented state.

Do not blindly assume that the first unchecked checkbox is correct.

---

# 14. Important distinction

Do not confuse:

"understanding the roadmap"

with:

"implementing the roadmap".

You may inspect the roadmap to determine what needs to be done.

But implementation must remain limited to exactly one selected roadmap item per task.

---

# 15. Stop condition

After completing and verifying one roadmap item:

STOP.

Do not start another roadmap item automatically.

Report:

* which roadmap item was completed
* what was changed
* what was verified
* any remaining limitations
* which roadmap item should be handled next

Then wait for the next task.

---

# 16. UI style and translation maintenance

For player-facing UI changes, follow STYLE_GUIDE.md. Reuse MenuStyle and UiText.
Keep player/character names and user chat untranslated. Translate custom HUD labels before measuring their width.
Update all six catalogs in src/main/resources/i18n/ whenever adding or changing UI/content phrases.
Use tools/translation-glossary.json for reviewed terminology; tools/update-translations.py --check verifies coverage without network or extra libraries.
The --refresh workflow uses offline translation models in a separate tooling cache; these models and Python must not become server runtime dependencies.
Review generated wording and preserve meaningful errors/dialogue while avoiding routine combat/gathering chat or action-bar spam.
Run the translation coverage tests and the resource-pack checks when their assets change. Do not claim in-client visual acceptance or large-player-count certification from unit tests alone.

# 17. Current product readiness and polishing state

Use PRODUCT_READINESS.md as the designated current roadmap-state and polishing file, as requested by the owner.
At task start, read its summary and the row/card relevant to the selected item, then verify that item against README.md and the actual code.
README.md remains the requirements source; current code and verified checks determine implementation status.
PRODUCT_READINESS.md distinguishes playable mechanics, foundations, missing gameplay/content, polishing and release acceptance. Do not treat a formula, database table or passing unit test as completion of the full player experience.
After implementation or polishing, update only the affected state rows/card, evidence, remaining work and next candidate. Keep historical details in AUDIT_STATE.md rather than duplicating a new state report each turn.
If README or an owner instruction changes, reconcile the affected state, preserve approved local changes and do not reintroduce cancelled mechanics from the remote historical version.
Continue to implement exactly one roadmap item or one targeted polishing issue per task and stop after verification.
