# Reasoning Framework Structure

> The anatomy of a well-structured reasoning framework — what it contains and how it teaches an agent to think.

---

## What a Reasoning Framework Is

Not a set of rules. Not a decision tree. Not a checklist. A structured way of seeing — a lens that tells the agent what categories of observation exist, what makes an observation significant, how to assess confidence, and when to say "I noticed something but I don't know what it means yet."

A reasoning framework teaches the agent what's worth noticing. Without it, the model still detects patterns. It just detects the wrong ones, or the irrelevant ones, or the ones that look interesting but don't mean anything in this context.

## The Components

### 1. Domain Context

What this agent is reasoning about and why it matters. Not instructions — orientation. The agent should understand the landscape before it starts interpreting data points.

"You are interpreting signals from client accounts. These signals help the business understand whether relationships are healthy, shifting, or at risk. Your interpretations feed into content targeting, outreach decisions, and strategic planning."

### 2. Signal Taxonomy

What kinds of things the agent might find. Each category has:

- **Definition** — what this signal type looks like in the data
- **Significance indicators** — what makes a signal of this type worth flagging
- **Interpretation guidance** — what this signal typically means, and what context changes the meaning
- **Common misreadings** — how agents typically misinterpret this signal type

Example categories for client intelligence: urgency signals, risk signals, opportunity signals, sentiment shifts, stakeholder changes, competitive threats, buying signals, expansion signals.

### 3. Confidence Calibration

What confidence means in this specific domain, with explicit criteria:

- **High (80-100%)** — multiple corroborating signals from recent, reliable sources. Direct evidence, not inference.
- **Medium (50-79%)** — some evidence but incomplete. Signals pointing in the same direction without conclusive proof. Some inference involved.
- **Low (20-49%)** — single data points, aged data, indirect inference, or conflicting signals. A hypothesis, not a conclusion.
- **Insufficient (<20%)** — not enough information to form even a hypothesis. State what was observed and what would be needed to assess further.

### 4. Decomposition Rules

How to break unstructured data into classified signals. CRM notes, meeting transcripts, email threads — these contain compressed information that needs to be pulled apart.

"A single note entry from a busy operator might contain four or five distinct signals compressed into a few sentences. Decompose each one. Classify it. Interpret it in context. A note that says 'Met with Sarah and new CFO, budget review pushed to Q3, they're also talking to CompetitorX about integration' contains: a stakeholder change (new CFO), a timeline shift (budget pushed), and a competitive signal (CompetitorX) — three distinct signals that should be classified and assessed separately."

### 5. Attribution Guidance

How to link signals to the right people and assess their significance based on role:

- Who said it? What's their role?
- Is this their pain or someone else's they're reporting?
- Are they a decision-maker, an influencer, or an observer?
- How reliable is their perspective? (A champion reports favourably. A detractor reports unfavourably. Neither is lying.)

### 6. Uncertainty Guidance

How to express partial knowledge usefully. Not "say you don't know" (that's a prohibition) — a structured way to communicate what was observed, what couldn't be determined, and what would need to be true for the hypothesis to hold.

"The output from a well-guided uncertain agent is often more valuable than a confident one. 'The opening was softened, but I'm not sure whether this is an audience-specific preference or a general tone shift. This is the third time I've seen it for this audience, but also the second time this week across all audiences.' That gives the system something to work with."

### 7. Pattern Recognition

What patterns are significant versus noise, and what thresholds matter:

- How many instances before a pattern is worth noting? (Minimum 3 for an emerging pattern, 5+ for confidence.)
- Over what timeframe? (3 similar signals in a week is different from 3 in a quarter.)
- What constitutes the "same" pattern? (Similar enough to group, different enough to not be duplicates.)
- When does a pattern warrant action versus continued observation?
