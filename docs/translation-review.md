# Chinese-to-English Translation Review

## Baseline and scope

The Chinese source is preserved in Git commit `7577bfec2d86ec816c108ac46fefba4ba5bcb7df`. The current execution version remains `2.1.0-draft`; the language migration does not introduce a new workflow version.

Compared source files:

- `SKILL.md`
- `references/delegation.md`
- `references/project-records.md`
- the original Chinese `README.md`

Reviewed targets are the English entry point, both English references, English `README.md`, and Chinese `README.zh-CN.md`. English is the execution-documentation language. File names, relative reference paths, task IDs, and task-state tokens retain their existing meanings.

## Review method

1. Freeze the Chinese files from the baseline commit before editing.
2. Translate the entry point and READMEs together; assign each reference to a separate translator.
3. Have a reviewer who did not translate the entry point trace its source requirements and review both READMEs. The core and README checklist contains 149 items.
4. Have the two reference translators independently cross-review each other's actual English files against the Chinese sources, covering every paragraph, bullet, table field, and template field. A translator's self-review is not a substitute for this comparison.
5. Check both directions: every source requirement must be represented, and every English-only directive must be justified rather than silently introducing behavior. Pay particular attention to permission versus obligation, defaults, conditions, ownership, scope, and acceptance authority.
6. Correct the findings and have the corresponding independent reviewer reread the changed passages.
7. Check YAML metadata, relative links, code fences, technical identifiers, table structures, and the language of execution files separately from semantic review.

## Semantic coverage

| Source area | Meaning retained in the English version |
| --- | --- |
| Skill metadata and primary role | Same applicability, direct handling of simple requests, MIT license, draft version, primary-agent decisions and final accountability, delegated maintenance and discovery, task-specific workflow, and stage-limited delivery. |
| Baseline establishment | Goals, users, deliverables, scope, constraints, observable acceptance, confirmed requirements versus assumptions, necessary clarification only, task directories, existing-record preservation, and reusable skill contents. |
| Git choice | Git by default for development; no Git by default for papers, research, and typesetting; mixed-task judgment; user/project choices; a conditional Git baseline and recorded gaps. |
| Approach and dependencies | Suitable methods, bounded autonomous resource discovery, trusted sources, fit and conditions of use, continuing without unsuitable resources, task-to-acceptance links, handoff agreements, explicit dependencies, and one maintained location per fact. |
| Team design and delegation | Roles derived from the actual task, adjustable headcount and participation stages, inspectable outputs, optional role combination, ready inputs, bounded concurrency, one writer, actual delegation, and accurate sequential fallback. |
| Execution and integration | Dependency order, review before accepted completion, delegated document updates, prompt decision/status reporting, coordinated ownership changes, failed-operation records, stopped-writer handoff, and task-appropriate milestones. |
| Acceptance and delivery | Artifact versions, real check methods/results/evidence, pass/fail/not-verified distinction, appropriate checks, user verification requirements, affected-check reruns, optional reliable evidence reuse, independent review, completion gates, gap disclosure, and resumable delivery records. |
| Recovery and changes | Read existing records; inspect deliverables, assignments, and live subagents; check the selected version system; reconcile facts without reinitialization; update changed requirements and affected work while preserving completed work. |
| Execution boundaries | Existing authorization still governs installation, connections, remote actions, publication, deployment, and external communication. Skill files do not expand tool permissions. |
| Delegation reference: role design and examples | Task-derived roles; optional ongoing duties; role/task-ID linkage; role count distinct from active concurrency; illustrative paper/development teams; confirmed experiment inputs; bounded resource discovery. |
| Delegation reference: task and report contracts | All brief and report fields, exact constraints and source material, minimum relevant context, readiness conditions, ready-for-review status rather than accepted completion, and designated report locations. |
| Delegation reference: shared work and repair | Single file ownership, delegated document maintenance, confirmed contract changes, shared-resource coordination, Git-conditional worktrees/index ownership, non-Git handoffs, stopped-writer transfer, integrated checks, and repair/reassignment rules. |
| Records reference: document ownership | PROJECT, PLAN, and AGENTS retain their distinct information, update triggers, delegated maintenance, primary decision/acceptance authority, and prohibition on complete duplicate records. |
| Records reference: templates | All PROJECT/PLAN/AGENTS sections, table columns, sample fields, task IDs, state meanings, canceled-task handling, actual evidence requirements, verified-method labels, and prevention of recursive kickoff are retained. |
| Records reference: version management | All four version-selection bullets and all six conditional Git steps are retained, including existing staged/unstaged protection, full proposed-commit inspection, accurate skeleton labeling, failure records, and both Git/non-Git recovery. |
| README parity | Both READMEs describe the same workflow, structure, installation choices, runtime requirements, scope limits, license, and language behavior. The example retains Chinese-language documentation, Chinese column names, local data, missing/duplicate checks, and an actual sample report. |

## Independent findings and corrections

All seven independent findings were corrected and reread by the reviewer who raised them.

| ID | Source distinction | Correction in the final English text |
| --- | --- | --- |
| C1 | “可以合并” permits combining responsibilities. | `You may combine responsibilities ...` preserves permission instead of making combination mandatory. |
| C2 | “可靠证据可复用” permits evidence reuse. | `You may reuse reliable evidence ...` preserves discretion. |
| C3 | “界面预览” means a user-interface preview. | `UI previews` avoids confusion with code or API interfaces. |
| D1 | A resource-discovery assignment must return candidates with reasons, or state that none were suitable. | `The worker must return ...` preserves the required result and the no-result alternative. |
| D2 | The brief must include the corresponding “原始说明,” which is broader than instructions alone. | `original source material` preserves the full scope of supporting material. |
| D3 | A short report message is restricted to status, locations, conclusions, and coordination issues. | `return only ... in the message` preserves that explicit restriction. |
| R1 | Inspect an existing repository and applicable conventions before deciding, to avoid accidental nesting. | `before making a decision, to avoid ...` removes the ambiguous reading of `before deciding to avoid ...`. |

Two further wording refinements clarify existing meanings: `small, narrowly scoped edits` translates “局部小改动”; `Defer a role until its required inputs are available` translates “暂未具备输入的职责稍后启动.” They do not add workflow conditions.

## Explicit language clarification and reader documentation

The one intentional operational clarification, discussed before the translation request, is:

> Communicate in the user's language. Follow the user's explicit language requirements for deliverables. The English used in these instructions and templates does not require English project documents or deliverables.

This makes the language policy explicit while retaining the task's requested output language. Bilingual README navigation, the updated file tree, and this review record are reader-documentation additions. They are not extra task phases or new subagent duties. Full Chinese execution instructions are preserved in Git history rather than duplicated in the active entry point.

## Structural checks

- The skill name, MIT license, and `2.1.0-draft` version are retained.
- YAML is parsed and required metadata is checked. The bundled Python validator could not run because PyYAML is unavailable; local YAML parsing is used for structural validation.
- Relative Markdown targets resolve, code fences balance, and template table column structures are preserved.
- Source inline technical identifiers remain present, including filenames and the unchanged `pending`, `in_progress`, `review`, `done`, and `blocked` task states where used.
- The three execution files contain English instructions; Chinese remains in the Chinese README, language-navigation labels, and quoted source fragments in this review.
- Git whitespace checks pass. The changes are limited to the language migration and its reader documentation.

These checks complement the independent bilingual review; structural checks alone do not establish semantic equivalence. The comparison found no unresolved translation discrepancy after the corrections. It does not measure whether English performs better than Chinese on live tasks.

## Reproduce the comparison

The original source can be inspected without placing a second execution version in the skill directory:

```bash
git show 7577bfec2d86ec816c108ac46fefba4ba5bcb7df:SKILL.md
git show 7577bfec2d86ec816c108ac46fefba4ba5bcb7df:references/delegation.md
git show 7577bfec2d86ec816c108ac46fefba4ba5bcb7df:references/project-records.md
git show 7577bfec2d86ec816c108ac46fefba4ba5bcb7df:README.md
```

## Reviewed target fingerprints

The following SHA-256 values identify the final reviewed execution files and READMEs. Later edits require reviewing the affected content again.

| File | SHA-256 |
| --- | --- |
| `SKILL.md` | `d5d704111b026d6ffae88d19f5eca63c18fc4a49b6b35f0dced81fee919e9571` |
| `references/delegation.md` | `28814a31b7c84a9697b1a21e26dfd4bb7da0a9adc99c41b4fa5bac9adde12fbe` |
| `references/project-records.md` | `ade6f030939e55dd44d81d24a4f3551ee2e3c33cf17852c0271b3ffcc5523373` |
| `README.md` | `c05e91c251f264d0b0765523a758b6a4d778428660a4c40eedffb273056026bc` |
| `README.zh-CN.md` | `360fd4c05ab860fd0627d76644db0893cab10b39f806d4c0ede35f67bdceada2` |
