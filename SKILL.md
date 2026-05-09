---
name: perspectives
description: Draft Microsoft "Perspectives" peer feedback by pulling 6 months of cross-collaboration evidence from the user's work data (WorkIQ MCP by default) and interviewing the user one question at a time with recommended answers grounded in the SBI (Situation-Behavior-Impact) framework, then composing constrained responses suitable for the peer's manager to read during performance review. Use when the user asks to write a Perspective, peer review, or peer feedback for a colleague at Microsoft.
argument-hint: [peer-name]
---

# Perspectives $ARGUMENTS

Help the user write Microsoft "Perspectives" peer feedback. The form has three sections; questions inside each section are ordered by importance. Earlier questions need substantive answers; later ones are nice-to-have and may be skipped. Never force an answer when there is no real content to back it up.

See [REFERENCE.md](REFERENCE.md) for worked examples, strong-vs-weak phrasings, and common pitfalls.

## Form

**Keep doing**
1. Here's something I think you do really well and hope you keep doing. *(required)*
2. Here's a suggestion for how you could leverage this strength further.

**Re-think**
1. Here's something you may want to re-think.
2. Here's an example to consider for doing it another way.

**Additional thoughts**
1. The thing I most value about working with you is.
2. Here are some other thoughts I have that you may want to consider.

## Workflow

### 1. Identify the peer
If `$ARGUMENTS` is non-empty, treat it as the peer's name (full name or alias) and use it directly. If only a partial name or alias was given, confirm the full name and alias with the user before proceeding. If `$ARGUMENTS` is empty, ask the user for the peer's full name and alias. Do not proceed without this.

### 2. Gather 6 months of evidence

**Default source: WorkIQ.** If the WorkIQ MCP server is wired up (e.g. `mcp__workiq__ask_work_iq` or equivalent), use it for everything in this step. WorkIQ is assumed to be available unless a call fails or the tool is missing.

**If WorkIQ is not available, fall back in this order:**

1. **Look for other connected sources** that can read the user's mail, calendar, Teams chats, and shared documents. Examples: a Microsoft Graph MCP server, an Outlook/Teams/SharePoint MCP, a generic email MCP, or any tool the user has explicitly granted access to communication media. Use whichever is wired up.
2. **If no suitable source is connected**, stop and ask the user which MCP, connector, or data source you should use for email and other communication media. Wait for their direction before continuing.

Do not attempt to draft from memory or invent evidence. If no source is reachable and the user has no preference, say so plainly and pause.

**Once you have a source, run targeted queries.** Bound every query with an explicit date range covering the last 6 months. Run a small set of focused queries rather than one broad one. Examples:

- Meetings I attended with <peer> in the last 6 months: purpose of each meeting and what <peer> contributed.
- Teams chats and emails between me and <peer> in the last 6 months: what <peer> proposed, pushed back on, or helped with.
- Documents <peer> authored or co-authored that I reviewed or commented on in the last 6 months.
- Interactions involving <peer>'s direct reports in the last 6 months where <peer> appears to have directed the work.

Keep concrete anchors as you go: project names, meeting titles, document titles, dates, and the specific action the peer took. These anchors are what turn vague praise into SBI-grounded feedback.

If a query turns up nothing or a source is unavailable, say so plainly and continue with what you can see. Do not invent evidence.

### 3. Categorize the material
Organize evidence into these buckets, keeping concrete anchors (project names, meeting titles, decisions, dates):

- Shared strategy, culture, points of common view.
- Collaborations on solutions or projects.
- Willingness to help; degree of effort contributed to assistance.
- Points of debate, pushback, offerings of alternate perspectives.

### 4. Interview the user, one question at a time
Walk the form top to bottom. For each question:

- Propose a recommended answer grounded in the categorized evidence, structured as **Situation → Behavior → Impact** (SBI). Name the meeting or project, what the peer did, and what changed because of it.
- If the evidence already answers the question, ask the user to confirm rather than asking open-ended.
- Resolve each branch before moving on.
- If a question has no substantive content, suggest skipping it.

### 5. Draft the responses

**Writing principles (read before drafting any response):**

- **Be specific.** Anchor every claim in a concrete situation. Vague praise ("great collaborator") is unusable; SBI ("In the X review you reframed Y, which unblocked Z") gives the peer something to act on.
- **Skip the mundane.** Identify what is uniquely valuable about this peer or the single skill gap that would most accelerate their growth. Generic competence does not earn a paragraph.
- **One thing per question.** Especially for Re-think, name one skill, not three. Multiple critiques dilute the signal.
- **Reframe gaps as skills to develop**, not personality labels. "An area worth investing in is X" rather than "You are too X."
- **Connect to impact.** Tie behavior to a tangible outcome: project shipped, customer trust grew, team unblocked, decision sharpened.
- **Lead with strengths in Keep-doing; offer alternatives in Re-think.** Frame Re-think as a perspective worth considering, not a verdict.
- **Use second person** ("You do X").
- **Avoid all-positive answers.** Skipping Re-think entirely leaves the peer unsupported. Find one substantive thing or skip the section deliberately, not by default.

**Output constraints:**

- Length: at most a modest paragraph per question.
- Punctuation: no hyphens, no em dashes, no emojis.
- Tone: professional, eloquent without being verbose, scoped to software industry vocabulary.
- Balance: positive responses should outnumber critical ones. The peer asked for the review; be honest but tempered.
- Constructive: even Re-think should help the peer improve, not just point out gaps.
- Audience: the peer's manager will read this and may use it for performance evaluation. Phrase accordingly.

Present each draft to the user for approval before finalizing.

## Privacy and handling

- The evidence you surface comes from the user's own mailbox and document permissions. Do not quote private conversations verbatim in the final draft; paraphrase to the level of detail the peer's manager would reasonably need.
- If a search turns up content the user clearly should not be drafting from (HR matters, sensitive personal information, content under legal hold), flag it and exclude it from the evidence pool.
- The final Perspective is shared with the peer's manager. Phrase every line with that audience in mind.
