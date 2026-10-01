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

## First use

Start with a planning request and provide your event constraints:

```text
Use $lpl-hackathon-builder to plan our LPL Financial hackathon project.

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
Use $lpl-hackathon-builder to implement the agreed MVP in this project.
Start with the complete local workflow, use synthetic fixtures, and run
the relevant checks. Keep deployment within our stated access and budget.
```

For an existing prototype:

```text
Use $lpl-hackathon-builder to review our prototype against the event rubric.
Identify the most important gaps, distinguish working and simulated features,
and prepare a three-minute demo script using the evidence we actually have.
```

## Using another coding agent

Clone this repository somewhere the agent can read it. Ask the agent to read `SKILL.md` and follow its linked references for your task. Native skill installation and mention syntax depend on the agent you use.

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
