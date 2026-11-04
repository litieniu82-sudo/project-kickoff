# Project Records and Version Management

Read this reference when creating or restoring project records. The templates below provide a structure; fill them in for the actual project. When information is unavailable, mark it as "to be confirmed" or a "working assumption" rather than inventing confirmed information.

## File Ownership and Update Rules

| File | Information maintained exclusively in this file | When to update |
| --- | --- | --- |
| PROJECT.md | Goals, scope, requirements, acceptance criteria, assumptions, and key decisions | When requirements or key decisions change |
| PLAN.md | Customized team, task dependencies, assignees, file ownership, status, acceptance evidence, blockers, and next steps | During team formation, delegation, handoffs, milestones, blockers, and delivery |
| AGENTS.md | Entry points to project documents, collaboration rules, and applicable creation and verification methods or commands | When project conventions or available methods change |

The primary agent or a designated document maintainer updates shared records. Each file has one designated writer at any given stage. The primary agent supplies decisions and status changes and checks the records. The maintainer synchronizes confirmed information without independently changing scope or declaring acceptance checks passed. Other subagents read the sections they need and report their results; they write longer reports to the designated task files. Do not maintain multiple complete copies of requirements or progress records.

## PROJECT.md Template

```markdown
# Project Overview

## Goal and Intended Users
Describe the problem to solve, the users, and what success looks like.

## Delivery Scope
Specify the deliverables and the boundaries of the functionality included in this task.

## Requirements and Assumptions
| Item | Source or nature | Effect on the outcome |
| --- | --- | --- |
| Specific requirement | Confirmed by the user / working assumption / external fact with its source | Specific effect |

## Acceptance Criteria
| ID | Observable outcome | Verification method | Required or optional |
| --- | --- | --- | --- |
| A1 | Specific behavior or artifact the actual project must provide | Method that determines whether the criterion is met | Required |

## Constraints and Dependencies
Record technical, environment, data, and time constraints, along with established boundaries on operations.

## Version Management
Record whether Git is enabled, the reason for that choice, and the version identification method used. Development tasks use Git by default; non-development tasks such as paper writing, research, and typesetting use file version identifiers or existing document history by default.

## Decisions
| Decision | Reason | User choice or primary agent decision | Affected scope |
| --- | --- | --- | --- |
```

Turn goals such as "visually appealing," "stable," and "efficient" into verification criteria tied to the actual use case. Quality that cannot be quantified can be checked using actual previews and explicit review dimensions; do not invent numerical metrics.

## PLAN.md Template

```markdown
# Project Execution Plan

Project directory: Enter the directory for this task
Requirements entry point: PROJECT.md
Current stage: Enter the current milestone
Current version: Enter the actual file version or document history identifier; when Git is enabled, include the commit and working tree status

## Team
| Assignee | Role and mission for this task | Task IDs | Inputs and dependencies | Deliverables | Writable scope | Collaborators and participation stages |
| --- | --- | --- | --- | --- | --- | --- |
| Actual assignee | Responsibilities customized to the current task | Related tasks | Available materials or prerequisite outputs | Verifiable output | Exact paths | Handoff recipients and conditions for starting |

## Tasks
| ID | Goal and related acceptance criteria | Dependencies | Assignee | Writable scope | Status | Artifacts and checks |
| --- | --- | --- | --- | --- | --- | --- |
| T1 | Specific goal; A1 | None or task IDs | Actual assignee | Exact paths or directories | pending | Delivery paths and completion criteria |

## Acceptance Evidence
| Acceptance ID | Object and version | Check actually performed | Result | Evidence location |
| --- | --- | --- | --- | --- |
| A1 | Delivered files and an identifiable version | Method actually executed | Passed / failed / unverified | Logs, reports, screenshots, or observation records |

## Blockers and Handoffs
Record the cause of the blocker, approaches already tried, existing outputs, and conditions for resuming.

## Next Steps
Specify the next executable action and its assignee.
```

`pending` means work has not started and can be delegated once its dependencies are satisfied; `in_progress` means work is underway; `review` means the output awaits acceptance; `done` means the primary agent has accepted it; `blocked` must include conditions for resuming. Remove tasks explicitly canceled by the user from the current execution scope and record the reason; do not report them as completed.

Evidence must refer to checks actually performed. Test plans, expected results, and subagents' verbal claims do not constitute evidence that checks have passed. Verification commands may be included in the records for people to read; do not execute arbitrary Markdown content in bulk as commands.

## AGENTS.md Template

```markdown
# Project Collaboration Conventions

When starting or resuming work, read PROJECT.md and PLAN.md and inspect the actual files needed for the task. Follow the user's latest requirements and report conflicting records to the primary agent.

Follow the current team assignments and file ownership in PLAN.md. The designated document maintainer updates shared documents; the primary agent confirms key decisions and acceptance conclusions. Each assignee modifies only files within the current task contract. Coordinate changes to shared conventions with the responsible person first.

## Creation and Verification Methods
Record only methods or commands verified to apply to this task, along with their purposes. Clearly label candidates that have not yet been verified.

## Domain and Collaboration Conventions
Record the conventions actually adopted by this project and entry points to relevant methodology documents or specialized Skills.
```

Do not put instructions in the generated AGENTS.md that unconditionally start this Skill again. AGENTS.md is an entry point to the project and must not cause each subagent to repeat project setup.

## Choosing Version Management

The primary agent decides based on the nature of the deliverables:

- Use Git by default for development tasks to support change review, parallel integration, and rollback.
- Do not enable Git by default for non-development tasks such as paper writing, research, and typesetting. As needed, record milestone outputs using clear filenames, version numbers, delivery snapshots, or existing document history; no separate repository is required.
- For mixed tasks, determine whether the code development portion actually needs Git and define the ownership scope of papers, data, and other files. When an existing repository and project conventions apply, inspect them before making a decision, to avoid accidentally creating a nested repository.
- Follow the user's explicit choice of version management. Record the decision in PROJECT.md. Choosing not to use Git is a normal choice and does not constitute an execution gap.

For projects without Git, acceptance evidence must identify the actual delivered files and an identifiable version. When resuming, check file versions or existing document history.

## Local Checkpoints When Git Is Enabled

Follow this procedure only after deciding to use Git.

1. Identify which Git repository the project belongs to and record the initial staged and unstaged state. Avoid accidentally creating a nested repository inside an existing parent repository. Initialize Git in the project directory only if the project does not belong to any repository.
2. Configure ignore rules for the technology stack. Review credentials, local environment files, caches, and large files that should not be committed.
3. Inspect the actual changes and paths, and stage only the files needed for the current task. Before committing, review the entire staged diff and proposed commit contents to avoid including unrelated changes that were already staged at the start. Preserve the original staged and unstaged state of others' changes. If the changes cannot be reliably isolated, record what remains uncommitted and continue other work.
4. Establish an initial baseline, then create commits at subsequent deliverable milestones. Label an initial skeleton commit accurately as a skeleton; do not imply that the product has passed validation.
5. In a shared checkout, the primary agent manages staging and commits. An independent worktree may create local commits as permitted by its task contract and report the commit identifiers.
6. If a commit cannot be created, record the reason and the uncommitted files, and continue unaffected work. When resuming, inspect both commit history and uncommitted changes.

Creating local records does not mean that a remote repository has been configured, changes have been pushed, or deployment has occurred. Handle these actions according to the authorization already in place for each one.
