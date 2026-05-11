---
name: perspectives
description: Draft Microsoft "Perspectives" peer feedback by pulling recent collaboration evidence from the user's work data (WorkIQ MCP by default), calibrating whether the interaction was deep or light, interviewing the user one question at a time, and composing manager-ready responses. Use SBI (Situation-Behavior-Impact) for deep collaborations and narrower context, observed contribution, and signal feedback for casual or limited peer interactions. Use when the user asks to write a Perspective, peer review, or peer feedback for a colleague at Microsoft.
argument-hint: [peer-name]
---

# Perspectives $ARGUMENTS

Help the user write Microsoft "Perspectives" peer feedback. The form has three sections; questions inside each section are ordered by importance. Earlier questions need substantive answers; later ones are nice-to-have and may be skipped. Calibrate the depth of feedback to the depth of interaction. Never force an answer when there is no real content to back it up.

See [REFERENCE.md](REFERENCE.md) for deep and light feedback patterns, worked examples, strong-vs-weak phrasings, and common pitfalls.

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

### 2. Calibrate interaction depth
Determine whether this should be **deep feedback** or **light feedback** before gathering evidence or drafting.

Use **deep feedback** when the user worked with the peer across a project, recurring meetings, shared deliverables, design reviews, incidents, planning, or sustained decision making.

Use **light feedback** when the user had limited direct interaction, such as a few meetings, a single review, light cross-team coordination, indirect exposure through documents, or a peer the user knows only casually.

If unclear, ask: "Was this a deep collaboration or a lighter interaction?" If the evidence later contradicts the initial choice, explain the mismatch and recalibrate with the user.

For light feedback:

- Do not force SBI.
- Do not force Re-think.
- Prefer a narrow, honest observation over a broad performance claim.
- Use framing such as "In the limited contexts where we worked together".
- Only mention impact that was directly visible to the user.

### 3. Gather evidence from the last 6 months

**Default source: WorkIQ.** If the WorkIQ MCP server is wired up (e.g. `mcp__workiq__ask_work_iq` or equivalent), use it for everything in this step. WorkIQ is assumed to be available unless a call fails or the tool is missing.

**If WorkIQ is not available, fall back in this order:**

1. **Look for other connected sources** that can read the user's mail, calendar, Teams chats, and shared documents. Examples: a Microsoft Graph MCP server, an Outlook/Teams/SharePoint MCP, a generic email MCP, or any tool the user has explicitly granted access to communication media. Use whichever is wired up.
2. **If no suitable source is connected**, stop and ask the user which MCP, connector, or data source you should use for email and other communication media. Wait for their direction before continuing.

Do not attempt to draft from memory or invent evidence. If no source is reachable and the user has no preference, say so plainly and pause.

**Once you have a source, run targeted queries.** Bound every query with an explicit date range covering the last 6 months. Run a small set of focused queries rather than one broad one.

For deep feedback, gather evidence across meetings, chats, emails, documents, and recurring collaboration patterns. Examples:

- Meetings I attended with <peer> in the last 6 months: purpose of each meeting and what <peer> contributed.
- Teams chats and emails between me and <peer> in the last 6 months: what <peer> proposed, pushed back on, or helped with.
- Documents <peer> authored or co-authored that I reviewed or commented on in the last 6 months.
- Interactions involving <peer>'s direct reports in the last 6 months where <peer> appears to have directed the work.

For light feedback, gather a narrower set of direct interactions only. Examples:

- Meetings or reviews where I directly interacted with <peer> in the last 6 months.
- Teams chats and emails between me and <peer> in the last 6 months.
- Documents from <peer> that I directly reviewed, commented on, or used.

Keep concrete anchors as you go: project names, meeting titles, document titles, dates, and the specific action the peer took. These anchors are what turn vague praise into appropriately grounded feedback.

If a query turns up nothing or a source is unavailable, say so plainly and continue with what you can see. Do not invent evidence.

### 4. Categorize the material
Organize evidence into these buckets, keeping concrete anchors (project names, meeting titles, decisions, dates):

- Shared strategy, culture, points of common view.
- Collaborations on solutions or projects.
- Willingness to help; degree of effort contributed to assistance.
- Points of debate, pushback, offerings of alternate perspectives.

For light feedback, only keep buckets supported by direct interaction. Do not infer broad collaboration patterns from thin evidence.

### 5. Interview the user, one question at a time
Walk the form top to bottom. For each question:

- For deep feedback, propose a recommended answer grounded in the categorized evidence and structured as **Situation → Behavior → Impact** (SBI). Name the meeting or project, what the peer did, and what changed because of it.
- For light feedback, propose a recommended answer using **Context → Observed contribution → Signal**. Name the limited context, describe what the peer did, and explain what that suggests without overstating impact.
- If the evidence already answers the question, ask the user to confirm rather than asking open-ended.
- Resolve each branch before moving on.
- If a question has no substantive content, suggest skipping it. Be especially willing to skip Re-think for light feedback unless there is a concrete observed behavior and a useful alternative to offer.

### 6. Draft the responses

**Writing principles (read before drafting any response):**

- **Calibrate to the relationship.** Use SBI for deep collaborations. Use limited-context observations for light interactions. Do not turn one meeting into a broad performance pattern.
- **Be specific.** Anchor every claim in a concrete situation or limited context. Vague praise ("great collaborator") is unusable; grounded feedback ("In the X review you reframed Y, which unblocked Z") gives the peer something to act on.
- **Skip the mundane.** Identify what is uniquely valuable about this peer or the single skill gap that would most accelerate their growth. Generic competence does not earn a paragraph.
- **One thing per question.** Especially for Re-think, name one skill, not three. Multiple critiques dilute the signal.
- **Reframe gaps as skills to develop**, not personality labels. "An area worth investing in is X" rather than "You are too X."
- **Connect to visible impact.** Tie behavior to a tangible outcome when the evidence supports it: project shipped, customer trust grew, team unblocked, decision sharpened. For light feedback, describe only the impact or signal the user could directly observe.
- **Lead with strengths in Keep-doing; offer alternatives in Re-think.** Frame Re-think as a perspective worth considering, not a verdict.
- **Use second person** ("You do X").
- **Do not default to all-positive deep feedback.** For deep collaborations, find one substantive Re-think item or skip deliberately. For light feedback, skip Re-think unless the user has enough direct evidence to make it fair and useful.

**Output constraints:**

- Length: at most a modest paragraph per question.
- Punctuation: no em dashes, no emojis.
- Tone: professional, eloquent without being verbose, scoped to software industry vocabulary.
- Balance: positive responses should outnumber critical ones. The peer asked for the review; be honest but tempered.
- Constructive: even Re-think should help the peer improve, not just point out gaps.
- Audience: the peer's manager will read this and may use it for performance evaluation. Phrase accordingly.

Present each draft to the user for approval before finalizing.

## Privacy and handling

- The evidence you surface comes from the user's own mailbox and document permissions. Do not quote private conversations verbatim in the final draft; paraphrase to the level of detail the peer's manager would reasonably need.
- If a search turns up content the user clearly should not be drafting from (HR matters, sensitive personal information, content under legal hold), flag it and exclude it from the evidence pool.
- The final Perspective is shared with the peer's manager. Phrase every line with that audience in mind.
