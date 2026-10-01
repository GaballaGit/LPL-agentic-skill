# LPL Hackathon Builder

An agent skill for planning, building, verifying, and pitching LPL Financial hackathon prototypes. It helps a coding agent choose a useful problem, keep the scope realistic, and demonstrate a complete workflow with evidence that it works.

The default stack is **Angular with TypeScript, ASP.NET Core, Kubernetes, AWS, and Terraform**. The skill prioritizes a working local application and adds infrastructure according to the event's requirements and available time.

The guidance uses public LPL sources and a user-provided stack. This is an independent project; its engineering recommendations are proposed practices, not verified LPL internal standards.

## What it helps with

- Comparing ideas against LPL's public priorities and existing offerings.
- Defining an MVP, architecture, acceptance criteria, and implementation plan.
- Building and checking a complete user journey, including failure recovery.
- Preparing a concise demo with measured results and clear integration boundaries.

The repository contains instructions and references. Application dependencies are chosen when a prototype is built. Installing the skill does not require AWS credentials, Kubernetes, Terraform, or a separate model API key.

## Installation

This repository is an [Agent Skills](https://agentskills.io/) style skill: a directory containing `SKILL.md` plus supporting `agents`, `assets`, and `references` folders. The same files can be installed into several agent harnesses.

## Setup in Codex

### Option 1: Ask the skill installer

In Codex, send:

```text
Use $skill-installer to install the lpl-hackathon-builder skill from
https://github.com/GaballaGit/LPL-agentic-skill.
The skill's SKILL.md is at the repository root.
```

### Option 2: Install manually

For macOS or Linux, run these commands in your terminal:

```bash
git clone https://github.com/GaballaGit/LPL-agentic-skill.git
cd LPL-agentic-skill
mkdir -p "$HOME/.agents/skills/lpl-hackathon-builder"
cp SKILL.md "$HOME/.agents/skills/lpl-hackathon-builder/"
cp -R agents assets references "$HOME/.agents/skills/lpl-hackathon-builder/"
```

This installs a personal skill available across your projects. On Windows, download or clone the repository and copy `SKILL.md`, `agents`, `assets`, and `references` into `%USERPROFILE%\.agents\skills\lpl-hackathon-builder`.

For a project-specific installation, copy the same files into `.agents/skills/lpl-hackathon-builder/` inside your hackathon project's root instead.

### Check that it is available

Open your hackathon project in Codex. Use `/skills` or type `$` and look for `lpl-hackathon-builder`. Invoke it explicitly with `$lpl-hackathon-builder`.

If it is missing, confirm that `SKILL.md` is directly inside the installed skill folder, that the supporting folders were copied, and that the skill is enabled. Start a new session after correcting the setup.

Installation and invocation guidance follows the [official OpenAI skill documentation](https://learn.chatgpt.com/docs/build-skills).

## Setup in pi

pi loads skills from `~/.pi/agent/skills/`, `~/.agents/skills/`, project `.pi/skills/`, and project `.agents/skills/` locations. Because the manual Codex install above uses `~/.agents/skills/lpl-hackathon-builder`, it is also available to pi.

To install into pi's native global skill folder instead, run:

```bash
git clone https://github.com/GaballaGit/LPL-agentic-skill.git
cd LPL-agentic-skill
mkdir -p "$HOME/.pi/agent/skills/lpl-hackathon-builder"
cp SKILL.md "$HOME/.pi/agent/skills/lpl-hackathon-builder/"
cp -R agents assets references "$HOME/.pi/agent/skills/lpl-hackathon-builder/"
```

For a project-specific pi install, copy the same files into `.pi/skills/lpl-hackathon-builder/` or `.agents/skills/lpl-hackathon-builder/` inside your project.

Restart pi or start a new session, then invoke the skill with:

```text
/skill:lpl-hackathon-builder plan our LPL Financial hackathon project
```

You can also ask pi in natural language to use the `lpl-hackathon-builder` skill.

## Setup in Claude Code

Claude Code commonly loads user skills from `~/.claude/skills/` and project skills from `.claude/skills/`. To install globally:

```bash
git clone https://github.com/GaballaGit/LPL-agentic-skill.git
cd LPL-agentic-skill
mkdir -p "$HOME/.claude/skills/lpl-hackathon-builder"
cp SKILL.md "$HOME/.claude/skills/lpl-hackathon-builder/"
cp -R agents assets references "$HOME/.claude/skills/lpl-hackathon-builder/"
```

For a project-specific Claude Code install, copy `SKILL.md`, `agents`, `assets`, and `references` into `.claude/skills/lpl-hackathon-builder/` inside the project.

Start a new Claude Code session after installing and ask:

```text
Use the lpl-hackathon-builder skill to plan our LPL Financial hackathon project.
```

## Using another coding agent

If your agent supports Agent Skills, install this repository as a skill directory named `lpl-hackathon-builder` with `SKILL.md` directly inside that directory. If it does not have native skill support, clone this repository somewhere the agent can read it and ask the agent to read `SKILL.md` and follow its linked references for your task. Native mention syntax depends on the agent you use.

## First use

Use the invocation style for your agent:

- Codex: `Use $lpl-hackathon-builder ...`
- pi: `/skill:lpl-hackathon-builder ...` or `Use the lpl-hackathon-builder skill ...`
- Claude Code and most other agents: `Use the lpl-hackathon-builder skill ...`
- Agents without native skill support: `Read SKILL.md in this repository and follow its linked references ...`

Start with a planning request and provide your event constraints:

```text
Use the lpl-hackathon-builder skill to plan our LPL Financial hackathon project.

Theme: [event theme, or open theme]
Time available: [hours]
Team: [size and experience]
Judging criteria: [paste the rubric, if available]
Required technologies: [requirements]
Available APIs and data: [resources]
AI restrictions: [restrictions]
Cloud access and budget: [access, or local only]
Submission requirements: [requirements]

Recommend one feasible concept, explain its value and differentiator,
and give us an MVP, acceptance criteria, architecture, and execution plan.
Do not write application code yet.
```

Then request implementation when you are ready:

```text
Use the lpl-hackathon-builder skill to implement the agreed MVP in this project.
Start with the complete local workflow, use synthetic fixtures, and run
the relevant checks. Keep deployment within our stated access and budget.
```

For an existing prototype:

```text
Use the lpl-hackathon-builder skill to review our prototype against the event rubric.
Identify the most important gaps, distinguish working and simulated features,
and prepare a three-minute demo script using the evidence we actually have.
```

## Included files

| File | Purpose |
| --- | --- |
| [SKILL.md](SKILL.md) | Main workflow and instructions |
| [agents/openai.yaml](agents/openai.yaml) | Codex interface metadata and invocation settings |
| [assets/icon.svg](assets/icon.svg) | Skill icon |
| [references/lpl-context.md](references/lpl-context.md) | Dated public sources, evidence boundaries, and candidate workflows |
| [references/engineering.md](references/engineering.md) | Proposed architecture, security, deployment, and verification practices |
| [references/demo-and-acceptance.md](references/demo-and-acceptance.md) | Acceptance examples, measurement guidance, and demo outline |

## Keeping it current

Update your clone with `git pull --ff-only`, then repeat the copy steps if you installed manually. Review the source dates in `references/lpl-context.md` before an event and supply the organizer's actual brief. Event requirements and explicit user instructions take precedence over the skill's defaults.

Use synthetic data for demonstrations. Clearly label mocked integrations, illustrative rules, and untested infrastructure; the skill does not provide access to LPL systems or establish regulatory compliance.
