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

The skill is split across two files on purpose: [`SKILL.md`](SKILL.md) is the workflow Copilot follows, and [`REFERENCE.md`](REFERENCE.md) is the worked examples and pitfalls Copilot consults while drafting. For the best experience, set it up once as an agent so you do not need to paste the files every time.

### Recommended: Create an agent in Microsoft 365 Copilot

Use [Agent Builder in Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder) for the lowest-friction setup. This creates a reusable declarative agent directly inside Microsoft 365 Copilot or Teams.

1. Open Microsoft 365 Copilot Chat from [microsoft365.com/chat](https://microsoft365.com/chat), [office.com/chat](https://office.com/chat), or the Microsoft 365 Copilot experience in Teams.
2. Select **New agent**.
3. Choose **Skip to configure**.
4. Name the agent `Perspectives`.
5. Paste the contents of [`SKILL.md`](SKILL.md) into **Instructions**.
6. Add [`REFERENCE.md`](REFERENCE.md) as a knowledge source by uploading it, or by selecting it from SharePoint if you store the file there.
7. In **Knowledge**, add the work-data sources your tenant allows:
   - **My emails**
   - **My Teams chats and meetings**
   - Relevant SharePoint files, folders, or sites
   - People in your organization, if available
8. Test the agent in the **Try it** tab.
9. Select **Create**.

To use it later, open the `Perspectives` agent and say:

> I want to write a Perspective for `<peer name and alias>`.

Agent Builder keeps the workflow and reference material attached to the agent, so later sessions can focus on the peer and the evidence instead of setup.

### Share it with others

After you create the agent, use **Share** to give access to specific people, groups, teams, or anyone in your organization, depending on your tenant policy. If you share the agent, each user still only gets results from content they are allowed to access.

### Requirements and limitations

- Agent Builder, email grounding, Teams grounding, People data, and SharePoint grounding depend on Microsoft 365 Copilot licensing and tenant admin policy.
- In Agent Builder, email knowledge is not currently scoped to a person or folder at setup time. The skill handles this by instructing Copilot to search by peer and explicit date range during the conversation.
- If your organization needs formal publishing, approval flows, custom actions, or additional channels, build the same agent in [Copilot Studio](https://learn.microsoft.com/en-us/microsoft-copilot-studio/publication-fundamentals-publish-channels) instead.

### Fallback: Paste both files into Copilot Chat

For a one-off, open Microsoft 365 Copilot Chat and paste **both** files as your first message, in this order:

1. The contents of [`SKILL.md`](SKILL.md).
2. A separator line such as `--- REFERENCE ---`.
3. The contents of [`REFERENCE.md`](REFERENCE.md).

Then say:

> Use these instructions. The reference material below the separator is for your use when drafting. I want to write a Perspective for `<peer name and alias>`.

Copilot will follow the workflow and pull from the reference content when drafting. This skips the Copilot Studio setup at the cost of re-pasting both files each session.

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
