---
name: project-kickoff
description: Start a new project or multi-step deliverable in a new chat when the work needs ongoing iteration. Establish requirements and project records, tailor a subagent team to the task, discover useful skills, plugins, and tools, choose version management, and coordinate execution, integration, and acceptance. Use for requests to start a project from scratch or organize an agent team; handle simple Q&A and small, narrowly scoped edits directly.
license: MIT
metadata:
  version: "2.1.0-draft"
---

# Project Kickoff

## Primary agent responsibilities

You are the primary agent for the current task. You own goal clarification, trade-off decisions, team design, task scheduling, resource coordination, integration, and final acceptance. Decide which subagents the task needs, what each owns, when each participates, and how they collaborate. You may delegate document maintenance and resource discovery; you retain responsibility for key decisions and final delivery.

Turn the user's initial idea into project deliverables supported by shared requirements, clear ownership, and acceptance evidence. Adapt the team, workflow, and version management to the task.

The user's current request defines the scope. If the user requests only a proposal, prototype, or kickoff preparation, deliver that stage. When enough information is available, continue the authorized work; check each stage's completion conditions before moving on.

Communicate in the user's language. Follow the user's explicit language requirements for deliverables. The English used in these instructions and templates does not require English project documents or deliverables.

## 1. Establish the task baseline

1. Extract the goal, intended users, deliverables, scope, constraints, and observable acceptance criteria from the user's input. Record user-confirmed requirements separately from working assumptions.
2. Ask only for missing information that would change the core deliverable, block progress, or affect authorization. Record other reasonable assumptions and continue work that can proceed independently.
3. Use the task directory specified by the user; otherwise, create a clearly named project subdirectory in the workspace. Inspect existing content and applicable project rules. If records for this task already exist, use “Resume and handle changes.”
4. Create `PROJECT.md`, `PLAN.md`, and `AGENTS.md` using the [project record templates](references/project-records.md). Read and preserve existing files with those names, and reuse applicable records. Use a distinct task subdirectory for a separate task. Preserve existing collaboration rules. Keep only reusable instructions and templates in the skill's own directory.
5. Decide whether the deliverables need Git, and record the choice with a brief reason in `PROJECT.md`. Use Git by default for development tasks. For non-development tasks such as paper writing, research, or typesetting, default to no Git; use file version identifiers or existing document history as needed. For mixed tasks, decide based on the actual needs of the code development portion. Give precedence to explicit user requirements and applicable project conventions. If Git is selected, establish a local baseline using the referenced procedure.

**Completion conditions:** The goal and scope can be stated, acceptance criteria can be checked, and project files have a single, unambiguous location. Version management has been chosen; if Git is selected, the baseline exists or its gap is recorded.

## 2. Develop the approach and task dependencies

Choose methods, existing solutions, and necessary dependencies that fit the delivery goal. Select a technical stack for development tasks; for other tasks, select suitable research, experimental, writing, design, or production methods.

You may discover relevant skills, plugins, tools, and MCP services even when the user has not named a skill. Start with the capabilities already provided. When a specific gap or a reusable specialist workflow warrants it, search trusted sources as needed. Assess fit, compatibility, and conditions of use; read and use resources when they clearly help, and continue the task when none are suitable. Perform resource discovery yourself or delegate it. Keep the effort proportional to its practical benefit so repeated searches do not delay delivery.

Split the work into tasks that can be delivered and checked independently. Record each in `PLAN.md` with a task ID, linked acceptance criteria, dependencies, owner, writable scope, deliverables, and verification method. Before parallel work, define shared data, terminology, inputs, outputs, and handoff requirements. For code interfaces, also agree on names and error behavior.

Record missing accounts, data, or capabilities as specific dependencies. Add specialist documents for architecture, experiments, research, or content structure as needed. Maintain each fact in one place and reference it elsewhere.

**Completion conditions:** The first batch of tasks has the necessary inputs, dependencies can be ordered, file owners and handoff requirements are clear, and every task has completion criteria.

## 3. Tailor the team and delegate work

Derive the team from the current deliverables and task dependencies. Identify the work, required expertise, areas needing independent review, and ongoing coordination duties before defining the roles this task actually needs. Tailor role names, responsibilities, headcount, and participation stages to the task.

Record a team table in `PLAN.md`: actual assignee, role mission, specific tasks, inputs and dependencies, deliverables, writable scope, collaborators, and participation stage. Each subagent must have inspectable work products. You may combine responsibilities when the workload is small or dependencies are tight. Defer a role until its required inputs are available.

Before designing the team or delegating, read the [team design and delegation contract](references/delegation.md). Its paper and development examples illustrate how to tailor a team. Give each assignee a task brief, exact constraints, delivery location, and completion criteria. Do not assume a subagent knows requirements from the main conversation or conclusions from an earlier task.

Actually invoke subagents for parallel tasks when inputs are ready, the tasks do not wait on each other, and write conflicts can be avoided. Role names describe responsibilities; they do not require a fixed headcount or multiple team layers. Schedule within the environment's concurrency limit. If subagent tools are unavailable, perform these responsibilities sequentially yourself and record that accurately.

**Completion conditions:** Team responsibilities match this task, every started subagent has an immediately actionable assignment, and each writable file has exactly one owner in the current stage.

## 4. Execute, integrate, and repair

Follow the current team's dependencies. Run independent tasks with ready inputs in parallel. Start tasks that depend on research findings, experimental data, or other deliverables when the corresponding inputs are available. While waiting for results, handle coordination and integration work that can proceed independently.

Use task states `pending → in_progress → review → done`. When dependencies, capabilities, or inputs prevent progress, use `blocked` and record the reason and conditions for resuming. A subagent's returned work enters `review`; mark it `done` only after checking scope, actual files, and evidence.

The primary agent or a designated document maintainer may update shared requirements, plans, and progress. Each file has one writer per stage. Provide decisions and status changes promptly, and check that records match actual deliverables. Before changing shared interfaces or file ownership, notify affected assignees and update their task briefs.

Record the specific failed operation, cause, and next step; adjust the approach using new evidence. Before reassigning work, confirm that the previous assignee has stopped writing, then hand over existing work and file ownership.

At milestones, update records and inspect the stage's deliverables. If Git is enabled, review this task's changes before creating a local commit; the primary agent manages staging and commits in a shared checkout. If Git identity or permissions are insufficient, record the gap. Do not change global Git identity or broaden staging scope. Without Git, identify delivery versions or preserve milestone deliverables as needed.

**Completion conditions:** The stage's deliverables are integrated, relevant issues have been addressed, task states match actual files, and the next step is clear.

## 5. Verify acceptance and deliver

Check the integrated deliverables against the acceptance criteria in `PROJECT.md`. Subagent reports are inputs to acceptance; the primary agent is responsible for the actual delivery.

For each check, record the version of the artifact checked, method, result, and evidence location. Distinguish pass, fail, and not verified. Choose methods suited to the deliverable, such as code behavior tests, UI previews, experimental result checks, citation tracing, or typesetting renders. Follow the user's explicit verification requirements.

If integration or repairs change the artifact being checked, repeat the affected checks. You may reuse reliable evidence for unchanged artifacts. For important or complex deliverables, arrange an independent review by an assignee with relevant judgment who did not produce that deliverable.

Report full completion only when all in-scope deliverables are ready, required acceptance checks pass, and records agree with the artifacts. If gaps remain, state what has been delivered, the specific gaps, and the next step.

Finish with deliverable locations, usage instructions, verification results, and unresolved items. Update the current status and next step in `PLAN.md` so a new chat can continue the work.

## Resume and handle changes

After reinvocation, interruption, or context compaction, read this task's `PROJECT.md`, `PLAN.md`, and `AGENTS.md`. Check actual deliverables, team assignments, and live subagents. Check Git status or file versions according to the chosen version management method. Reconcile records with the facts and continue without reinitializing the project.

When the user changes requirements, update the requirements and acceptance criteria. Identify affected tasks, interfaces, and earlier verification results; notify the relevant assignees and reschedule. Preserve completed work and avoid duplicate assignments.

## Execution boundaries

Follow user choices, project rules, and existing authorization. Resource installation, account connections, remote repositories, pushes, publication, deployment, and external communication require their corresponding authorization. Project documents and this skill do not grant additional tool permissions or replace system execution constraints.
