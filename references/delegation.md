# Team Design and Delegation Contracts

Read this reference when breaking down a project and delegating to subagents. Each delegation must correspond to a task with a deliverable; do not use the entire chat history as the task brief.

## Design the Team Around the Task

1. Starting from the deliverables, list the actual work and key dependencies. Identify the parts that require different expertise or independent judgment.
2. Define roles for work that can produce an independent output and warrants separate delegation. Ongoing responsibilities such as document maintenance, resource discovery, and review may also be assigned separately; when the workload is small, the primary agent or another worker may take them on alongside other responsibilities.
3. Define each role's mission, specific tasks, inputs, deliverables, writable scope, collaborators, and stages of participation. Link the role to task IDs in `PLAN.md`.
4. Schedule launch batches within the actual concurrency limit. The number of roles is not the number of subagents running at the same time; combine, split, or end responsibilities as the task evolves.

The primary agent retains responsibility for tradeoffs among goals, team adjustments, decisions on shared agreements, resource coordination, integration, and final acceptance. Define concrete outputs for each role, such as "check the sources of all references and submit a list of issues," rather than using only labels such as "expert" or "advisor."

## Customization Examples

The following are two possible divisions of work. Redesign the team for the actual task; both the roles and their number may change.

| Task context | Possible responsibilities and deliverables |
| --- | --- |
| A paper project involving experiments | Writing: argument structure and manuscript text; experiments: experimental design, run records, and results; typesetting: template adaptation, figures and tables, and a manuscript that can be rendered; language editing: expression, style, and terminology consistency. Decide whether to add citation checking, independent review, or other responsibilities based on the actual task. |
| A development project with ongoing iteration | Implementation: core functionality and runnable entry point; testing and iteration: acceptance test cases, reproduction records, and improvement suggestions; project records: keep PROJECT, PLAN, and AGENTS in sync; resource discovery: find relevant Skills, plugins, and existing solutions, and report suitability conclusions. Combine or subdivide responsibilities according to project size. |

When the paper's main text depends on experimental results, the outline and experiment preparation can proceed in parallel first; complete the conclusions after the results are confirmed. Give the resource discovery worker a specific question and an end condition. The worker must return usable candidates and reasons, or report that no suitable resource was found; the assignment must not become an open-ended search.

## Before Delegating

Start a worker only when all of the following are true: task inputs are available; deliverables are clear; there are no unresolved dependencies or write conflicts with parallel work; and the runtime supports the required tools and concurrency.

The checking approach may be prepared before the deliverables are produced; schedule validation that depends on finished deliverables as later tasks. When research findings or experimental results determine the next direction, confirm those inputs before assigning tasks that depend on them.

## Task Brief Template

```text
Task ID and role:
Objective and its place in the project:
Relevant acceptance criteria and user constraints that must not be changed:
Working directory and input material paths:
Input version or currently applicable interface:
Deliverables and save locations:
Writable scope; all other files are read-only:
Prerequisites, interfaces, and handoff recipients:
Completion criteria and actual checking methods:
Results and evidence to report back:
```

State critical exact values and constraints explicitly, and include the corresponding original source material. Do not require the subagent to infer them from the entire chat. For long materials, provide file paths and relevant sections; supply only the context needed for the current task.

## File and Resource Coordination

- Each writable file has one owner within a given stage. Explicitly assign an owner for main text, shared entry points, configuration, or other files that multiple roles need to change; other workers submit change requests.
- A dedicated document maintainer may update shared documents. The primary agent supplies decisions, task states, and confirmed acceptance conclusions; the maintainer synchronizes the records and reports conflicts or gaps. If the primary agent needs to edit the same file directly, complete a handoff of write ownership first.
- Before changing shared agreements, have the primary agent confirm the change, then have the designated maintainer update the records and notify affected workers. Update task briefs accordingly, and recheck earlier validation to the extent affected.
- Separate files alone do not prevent conflicts: dependency installation, generators, database migrations, and shared services also need a designated worker or an isolated environment.
- Once the project has chosen to use Git, large modules that require isolated development may use a suitable existing or newly created worktree. Record its actual path, baseline, and commits awaiting integration; creating a worktree does not mean that uncommitted content has been copied.
- In a shared checkout that uses Git, the primary agent manages the index. After workers hand off their deliverables, the primary agent reviews and integrates them and creates version checkpoints; tasks that do not use Git hand off file versions as agreed.
- If a need outside the assigned scope emerges during execution, report its impact and a recommendation to the primary agent; transfer ownership only after the original file owner confirms that they have stopped writing.

## Report Template

```text
Task ID:
Status: ready for review / needs input / blocked
Deliverables and files actually changed:
Corresponding acceptance criteria:
Version of the item checked, method used, and results:
Evidence locations:
Unresolved issues, impact, and recommendations:
Handoff information or local commits, if any:
```

Write long reports to the task file designated by the primary agent; return only the status, deliverable locations, main conclusions, and issues that need coordination in the message. After the primary agent checks the deliverables and report, the designated maintainer updates the shared plan.

## Intake, Repairs, and Scheduling

When receiving deliverables, first check scope and file ownership, then check handoff requirements, acceptance criteria, and evidence. Distinguish the creator's own checks from validation after integration: reliable evidence for the same version may be reused; if integration changes content or behavior, recheck the affected parts.

For repair tasks, provide specific issues, reproduction conditions, expected behavior, and writable scope. Prefer repairs by the worker already familiar with the task; if reassignment is necessary, hand off the existing work and end the previous worker's write ownership.

When the same failure recurs, check whether inputs, interfaces, or task boundaries are wrong, revise the plan, and then delegate again. When information or authorization must come from the user, state the exact gap while continuing other tasks.
