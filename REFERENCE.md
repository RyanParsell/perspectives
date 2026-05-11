# Perspectives Reference

Worked examples, strong-vs-weak phrasings, and common pitfalls. Load this when drafting responses or when the user wants tighter language.

## Deep feedback: SBI structure

Use **Situation → Behavior → Impact** for deep collaboration feedback. A deep feedback response should be reducible to:

- **Situation**: when and where it happened (a meeting, a project, a review, a launch)
- **Behavior**: what the peer specifically did or said
- **Impact**: what changed because of it (a decision sharpened, a team unblocked, a customer outcome, a risk averted)

If a deep feedback draft is missing any of the three, the response will read as vague.

### Example skeleton for "Keep doing"

> During the [project / review / decision], you [specific behavior]. The result was [tangible outcome]. This strength shows up consistently when [pattern across multiple situations].

### Example skeleton for "Re-think"

> One area worth investing in is [single skill]. In [specific situation] you [behavior]. An alternative to consider is [different approach], which would [expected impact]. Your [existing strengths] are already strong enough to support this shift.

## Light feedback: context, observed contribution, signal

Use this when the interaction was real but limited. The goal is to be useful without overstating what the user actually saw.

- **Context**: where the interaction happened
- **Observed contribution**: what the peer did that stood out
- **Signal**: what that suggests, without claiming a broad pattern

### Example skeleton for light "Keep doing"

> In the limited contexts where we worked together, especially [meeting / review / thread], you [observed contribution]. That helped me [visible effect]. My feedback is based on a narrow slice of your work, but the signal I saw was [specific strength].

### Example skeleton for light "Re-think"

> I do not have enough direct exposure to offer a fair Re-think item. Based on the limited work we shared, the most useful feedback I can give is to keep leaning into [observed strength].

Only write a light Re-think when there is a concrete observed behavior and a useful alternative. Otherwise, skip it.

## Strong vs weak phrasings

### Keep doing

| Weak | Strong |
| --- | --- |
| You are a great collaborator. | In the Q3 platform review, you reconciled the conflicting proposals from the data and ingestion teams into a single migration path. The result was a decision the room could support, where two prior meetings had stalled. |
| You write good code. | Your reviews on the auth refactor caught two race conditions before they reached staging. Beyond catching defects, your reviews teach the patterns behind them, which is why several engineers now mirror that style. |
| You always help others. | When the SRE on call escalated the partition outage, you joined inside ten minutes despite being out of rotation, walked the responder through the recovery, and stayed until the postmortem owner was identified. |

### Light keep doing

| Weak | Strong |
| --- | --- |
| We have not worked together much, but you seem great. | In the limited contexts where we worked together, especially the platform planning discussion, you were clear and practical in how you surfaced tradeoffs. That helped me understand the decision space quickly. My feedback is based on a narrow slice of your work, but the signal I saw was strong. |
| I only saw you in one meeting, so I do not have much feedback. | My direct exposure to your work has been limited to the API review thread, but your comments there were precise and grounded in customer impact. You identified the part of the proposal that would create operational ambiguity and suggested a cleaner owner boundary. That was a useful contribution even from a small interaction. |

### Suggestion to leverage strength further

| Weak | Strong |
| --- | --- |
| Keep doing what you are doing. | Consider running a recurring brown bag on review craft. The patterns you reinforce one PR at a time would compound faster as a shared vocabulary across the org. |

### Re-think

| Weak | Strong |
| --- | --- |
| You should communicate better. | One area worth investing in is framing technical proposals for non-engineering audiences. In the compliance review for the telemetry change, the engineering leads followed the architecture-first explanation, but the compliance reviewers needed two follow-up meetings to land the basics. Opening with the business outcome before the system design would let the same content reach a wider room in one pass. |
| You take on too much. | A pattern worth examining is the volume of in-flight commitments you carry. Across the last quarter, three of the workstreams you owned slipped because earlier work expanded. Saying no earlier, or naming the tradeoff explicitly when scope arrives, would protect both the work and your credibility on delivery dates. |

### Light Re-think

| Weak | Strong |
| --- | --- |
| You should probably communicate better, but I am not sure. | I do not have enough direct exposure to offer a fair Re-think item. Based on the limited work we shared, the most useful feedback I can give is to keep making your tradeoff analysis as explicit as it was in the planning discussion. |
| In our one meeting, you talked too much. | I only saw a small slice of your collaboration style, so I would frame this lightly: in the design review, the room moved faster once the proposal was summarized around the decision needed rather than the full technical history. Continuing to lead with the decision point would make your input land even faster in rooms that have less context. |

### Example to consider

| Weak | Strong |
| --- | --- |
| Try doing it differently next time. | When the design partner pushed back on the proposed schema, you defended the original approach in detail. An alternative worth trying is to spend the first ten minutes treating the pushback as data and asking what the partner sees that you do not, before defending. The teams who do this tend to land at the same answer faster, with the partner feeling heard. |

### The thing I most value

| Weak | Strong |
| --- | --- |
| You are smart and easy to work with. | What I value most is your willingness to surface the inconvenient question early. Several times this year you have asked the question that the room was avoiding, which has saved cycles that would have been spent later unwinding decisions made on shaky assumptions. |

## Common pitfalls

- **Vague praise or critique**: "great teammate", "needs to communicate better". Always anchor to a situation.
- **Personality labels instead of behaviors**: "You are disorganized" violates SBI. "Responses to urgent requests have arrived a day or two late on three recent occasions" is actionable.
- **Burying the message in narrative**: long, balanced paragraphs let the reader miss the point. State the takeaway, then support it.
- **Multiple weaknesses in Re-think**: pick one. The single skill that would most unlock growth.
- **All-positive deep Perspectives**: skipping Re-think on default reads as either disengaged or as withholding. Find one substantive thing or skip deliberately.
- **Manufacturing Re-think**: for light feedback, skip Re-think unless there is a concrete observed behavior and a useful alternative to offer.
- **Overclaiming from limited exposure**: do not turn one good meeting into a broad claim about performance. Use limited-context framing or skip the question.
- **Repeating what the manager already sees**: surface what only a peer would know. Cross-team collaboration patterns, debate quality, willingness to help when no one is watching.
- **Framing critique as judgment**: "you are wrong about X" closes the conversation. "An alternative worth considering is X because Y" opens it.
- **Forgetting the audience**: the peer's manager will read this. Anything that reads as personal or off-topic for performance evaluation does not belong.
- **Quoting private channels verbatim**: the evidence you surface from mail and chat is for grounding your judgment, not for paste-through. Paraphrase to the level of detail the manager needs.

## Length calibration

- Modest paragraph: roughly three to five sentences.
- If a response is shorter than two sentences, it is probably too vague.
- If it is longer than six sentences, it is probably mixing multiple points or burying the message.

## Voice

- Second person throughout. "You" rather than "they" or "this person".
- Active voice for behavior. "You raised the concern" rather than "the concern was raised".
- Past tense for situations, present tense for ongoing strengths.
- Limited-context framing for light feedback. "In the limited contexts where we worked together" is better than pretending broad exposure.

## When to skip a question

Skip rather than fill when:

- You have no concrete situation to anchor the response.
- The honest answer would be a generic platitude.
- The point you would make has already been made better in an earlier question.
- The relationship is light and the only possible Re-think would be speculative.

A blank answer with a strong earlier answer is better than a thin answer in every box.
