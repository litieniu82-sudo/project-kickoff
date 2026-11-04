# Project Kickoff

English | [简体中文](README.zh-CN.md)

An AI agent skill for starting multi-step tasks in a new chat. The primary agent designs a team around the specific goal, coordinates execution, and takes responsibility for integrated deliverables and final acceptance.

Current version: `2.1.0-draft`. Execution instructions are in English. Communicate in the user's language and follow the user's explicit language requirements for deliverables. Suitable tasks include development, research, paper writing, and content production that need ongoing iteration.

## How it works

- **Start with the goal:** Define delivery scope, constraints, working assumptions, and checkable acceptance criteria.
- **Tailor the team to the task:** Derive roles, headcount, responsibilities, and start order from the actual work. Engineering, experiments, writing, typesetting, document maintenance, and resource discovery are possible responsibilities.
- **Discover resources as needed:** Find relevant skills, plugins, tools, and existing solutions; adopt them when they provide practical value.
- **Choose version management:** Use Git by default for development tasks. For non-development work such as papers, research, and typesetting, default to file versions or existing document history.
- **Keep project records:** Use PROJECT.md, PLAN.md, and AGENTS.md to record goals, the team, progress, and collaboration rules so interrupted work can resume.
- **Verify acceptance with evidence:** Subagents deliver inspectable artifacts and verification records; the primary agent integrates and confirms delivery.

## Repository structure

```text
project-kickoff/
├── SKILL.md
├── references/
│   ├── delegation.md
│   └── project-records.md
├── docs/
│   └── translation-review.md
├── README.md
├── README.zh-CN.md
├── LICENSE
└── .gitignore
```

`SKILL.md` is the execution entry point. `references` contains delegation rules and project record templates to read as needed. Preserve the complete skill directory and relative paths when using or moving it. The READMEs and translation review are reader documentation, outside the execution instructions.

## Get and install

Clone over HTTPS:

```bash
git clone https://github.com/litieniu82-sudo/project-kickoff.git
```

Alternatively, download and extract a ZIP. Install the complete `project-kickoff` folder in a skill directory supported by your client, or provide this repository's address to a client that supports installing skills from GitHub.

## Usage example

Explicitly invoke the installed skill in Codex and describe the task:

```text
$project-kickoff

Goal: Develop a local CSV data checking tool.
Deliverables: A runnable tool, Chinese-language instructions, and a sample report.
Constraints: Support Chinese column names and keep the data local.
Acceptance: Use sample data to check missing values and duplicate records, and show the actual report.

Tailor the agent team to the task, establish project records, and continue until the deliverables within this request's scope are complete.
```

The skill also supports non-development tasks. For a paper, assign literature verification, experiments, writing, typesetting, and language editing as needed. If the user requests only a proposal, prototype, or kickoff preparation, limit execution to that stage.

## Runtime requirements

The client must support reading `SKILL.md` and its relative references. Actual parallel work requires subagent tools; otherwise, the primary agent performs the needed responsibilities sequentially. Git is required only when selected for the task's version management.

## Translation review

See the [Chinese-to-English comparison record](docs/translation-review.md) for the source baseline, semantic review coverage, and language clarification.

## License

This project uses the [MIT License](LICENSE). You are welcome to use, modify, and share it under that license.
