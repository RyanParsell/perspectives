# Perspectives

A Microsoft 365 Copilot skill for writing **Microsoft "Perspectives" peer feedback**.

Perspectives is the peer feedback form Microsoft employees fill out for one another during the performance review cycle. The free-form text fields are easy to fill with platitudes ("great collaborator", "always helpful") and hard to fill with feedback that the peer's manager can actually use. This skill walks Copilot through the process of producing the latter.

## What it does

1. **Asks for the peer.** Full name and alias.
2. **Pulls 6 months of real evidence** from the user's own Microsoft 365 graph: Outlook mail, Teams chats, calendar, SharePoint and OneDrive documents, Loop, Planner.
3. **Categorizes** the material into shared strategy, collaboration, willingness to help, and points of debate.
4. **Interviews the user one question at a time**, proposing a draft for each Perspectives question grounded in the evidence and structured as **Situation → Behavior → Impact** (SBI).
5. **Drafts the responses** under tight constraints — one substantive point per question, no em dashes, audience is the peer's manager.

The result is feedback the peer's manager can read during performance evaluation and walk away with a sharper picture of the peer than they had before.

## Why SBI

Most peer-feedback advice collapses to one rule: anchor every claim in a specific situation and tie the behavior to a tangible outcome. The skill enforces this through the **Situation → Behavior → Impact** framework. Vague praise ("you write good code") becomes evidence the manager can act on ("your reviews on the auth refactor caught two race conditions before they reached staging, and several engineers now mirror that style").

`REFERENCE.md` contains worked examples of weak vs strong phrasings, common pitfalls, and length calibration.

## How to use it with Microsoft 365 Copilot

You have a few options depending on how often you write Perspectives and how much setup you want to do.

### Option 1: Paste as a system prompt in Copilot Chat
Open Microsoft 365 Copilot Chat, paste the contents of [`SKILL.md`](SKILL.md) as your first message, then say:

> Use these instructions. I want to write a Perspective for `<peer name and alias>`.

Copilot will follow the workflow: gather evidence from your Microsoft 365 data, categorize it, and interview you one question at a time.

### Option 2: Build a declarative agent in Copilot Studio
Use [`SKILL.md`](SKILL.md) as the instructions for a custom agent in Copilot Studio. Add `REFERENCE.md` as a knowledge source the agent can pull from when drafting. This gives you a reusable agent you can invoke directly when review season comes around.

### Option 3: Save as a Copilot Lab prompt
Trim [`SKILL.md`](SKILL.md) down to the workflow steps and save it as a personal prompt in Copilot Lab. Run it whenever you need to write a Perspective.

## What's in this repo

| File | Purpose |
| --- | --- |
| [`SKILL.md`](SKILL.md) | The instructions Copilot follows: form structure, evidence-gathering sources, interview workflow, writing principles, output constraints. |
| [`REFERENCE.md`](REFERENCE.md) | Worked examples (strong vs weak phrasings), the SBI skeleton, common pitfalls, length and voice calibration. |
| `LICENSE` | MIT. |

## Privacy

The skill draws only from data the user already has access to in their own Microsoft 365 tenant. The final draft is meant to be read by the peer's manager during performance review. The skill instructs Copilot to paraphrase private conversations rather than quote them verbatim, and to flag and exclude content that should not be drafted from (HR matters, sensitive personal information, content under legal hold).

## License

MIT. See [`LICENSE`](LICENSE).
