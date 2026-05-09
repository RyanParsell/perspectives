# Perspectives

A coding-assistant skill for writing **Microsoft "Perspectives" peer feedback**.

Perspectives is the peer feedback form Microsoft employees fill out for one another during the performance review cycle. The free-form text fields are easy to fill with platitudes ("great collaborator", "always helpful") and hard to fill with feedback that the peer's manager can actually use. This skill walks the assistant through the process of producing the latter.

## What it does

1. **Asks for the peer.** Full name and alias.
2. **Pulls 6 months of real evidence** from the user's own work data via the [WorkIQ](https://www.microsoft.com/en-us/microsoft-365/work-iq) MCP server: Outlook mail, Teams chats, calendar, SharePoint and OneDrive documents.
3. **Categorizes** the material into shared strategy, collaboration, willingness to help, and points of debate.
4. **Interviews the user one question at a time**, proposing a draft for each Perspectives question grounded in the evidence and structured as **Situation → Behavior → Impact** (SBI).
5. **Drafts the responses** under tight constraints: one substantive point per question, no em dashes, audience is the peer's manager.

The result is feedback the peer's manager can read during performance evaluation and walk away with a sharper picture of the peer than they had before.

## Why SBI

Most peer-feedback advice collapses to one rule: anchor every claim in a specific situation and tie the behavior to a tangible outcome. The skill enforces this through the **Situation → Behavior → Impact** framework. Vague praise ("you write good code") becomes evidence the manager can act on ("your reviews on the auth refactor caught two race conditions before they reached staging, and several engineers now mirror that style").

[`REFERENCE.md`](REFERENCE.md) contains worked examples of weak vs strong phrasings, common pitfalls, and length calibration.

## Requirements

- A coding assistant: **Claude Code**, **OpenAI Codex CLI**, or **GitHub Copilot** (VS Code).
- An MCP-accessible source for the user's mail, calendar, Teams chats, and shared documents. **[WorkIQ](https://www.microsoft.com/en-us/microsoft-365/work-iq)** is the default and what the skill is tuned for. Any equivalent Microsoft Graph / M365 MCP also works; if none is wired up, the skill will ask which source to use.

## How to deploy it

The skill is split across two files: [`SKILL.md`](SKILL.md) is the workflow the assistant follows, and [`REFERENCE.md`](REFERENCE.md) is the worked examples and pitfalls it consults while drafting. Pick the deployment path that matches your assistant.

### Claude Code

Copy both files into your user-scoped skills directory.

```powershell
# Windows (PowerShell)
$dest = "$env:USERPROFILE\.claude\skills\perspectives"
New-Item -ItemType Directory -Force -Path $dest | Out-Null
Copy-Item SKILL.md, REFERENCE.md $dest
```

```bash
# macOS / Linux
mkdir -p ~/.claude/skills/perspectives
cp SKILL.md REFERENCE.md ~/.claude/skills/perspectives/
```

Then in any Claude Code session:

> /perspectives `<peer name and alias>`

Or just describe the task ("write a Perspective for `<peer>`") and the skill will trigger from its description.

### OpenAI Codex CLI

Codex Skills use the same `SKILL.md` format as Claude Code. Drop both files into the user-scoped skills directory.

```powershell
# Windows (PowerShell)
$dest = "$env:USERPROFILE\.codex\skills\perspectives"
New-Item -ItemType Directory -Force -Path $dest | Out-Null
Copy-Item SKILL.md, REFERENCE.md $dest
```

```bash
# macOS / Linux
mkdir -p ~/.codex/skills/perspectives
cp SKILL.md REFERENCE.md ~/.codex/skills/perspectives/
```

Then in Codex (CLI or IDE extension):

> /perspectives `<peer name and alias>`

Codex will load the full `SKILL.md` when it decides to use the skill (progressive disclosure based on the description).

### GitHub Copilot (VS Code)

This repo ships a Copilot prompt file at [`.github/prompts/perspectives.prompt.md`](.github/prompts/perspectives.prompt.md) that drives the workflow.

**Easiest path: use the cloned repo as the workspace.**

1. Clone this repo and open it in VS Code with GitHub Copilot enabled.
2. In Copilot Chat, type `/perspectives` and add the peer's name and alias.

The prompt file references `SKILL.md` and `REFERENCE.md` from the workspace root, so as long as you opened the cloned repo, Copilot has everything it needs.

**Alternative: drop the prompt into another workspace.** Copy all three files into your target workspace at:

- `.github/prompts/perspectives.prompt.md`
- `SKILL.md`
- `REFERENCE.md`

Then invoke `/perspectives` from Copilot Chat in that workspace.

> Note: Copilot prompt files require VS Code with GitHub Copilot. The `mode: agent` frontmatter in the prompt file allows Copilot to call MCP tools (including WorkIQ) during the workflow.

## What's in this repo

| File | Purpose |
| --- | --- |
| [`SKILL.md`](SKILL.md) | Canonical workflow the assistant follows: form structure, evidence-gathering steps, interview workflow, writing principles, output constraints. Format works as a Claude Code skill and a Codex skill. |
| [`REFERENCE.md`](REFERENCE.md) | Worked examples (strong vs weak phrasings), the SBI skeleton, common pitfalls, length and voice calibration. |
| [`.github/prompts/perspectives.prompt.md`](.github/prompts/perspectives.prompt.md) | GitHub Copilot prompt file. References `SKILL.md` and `REFERENCE.md` from the workspace. |
| `LICENSE` | MIT. |

## Privacy

The skill draws only from data the user already has access to in their own Microsoft 365 tenant, surfaced through whichever MCP source the user has wired up (WorkIQ by default). The final draft is meant to be read by the peer's manager during performance review. The skill instructs the assistant to paraphrase private conversations rather than quote them verbatim, and to flag and exclude content that should not be drafted from (HR matters, sensitive personal information, content under legal hold).

## License

MIT. See [`LICENSE`](LICENSE).
