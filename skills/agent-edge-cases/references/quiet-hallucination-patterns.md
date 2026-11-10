# Quiet Hallucination Patterns

> The specific ways agents misread systems without operational guidance — not dramatic fabrication, but compounding inaccuracy.

---

## What Quiet Hallucination Is

Quiet hallucination isn't making things up. It's misreading what's there. The agent queries a system, gets real data, and misinterprets it in ways that look authoritative. The output is technically derived from actual records. It's still wrong.

These aren't dramatic failures. They're compounding inaccuracies — each one small, each one plausible, and together they make the entire output unreliable.

## The Patterns

### Pagination Blindness

The agent calls an API, receives the first page of results, and treats it as the complete dataset. "There are 25 contacts matching this criteria" when there are actually 250 — the agent read page 1 of 10 and never checked for more.

This compounds when the agent draws conclusions from an incomplete dataset: "The most common job title is VP Engineering" — true for the first 25, completely wrong for all 250.

### Inference from Training Data

The agent recognises an entity and fills in details from its training data instead of the actual record. It sees "Salesforce" as a company name and starts referencing Salesforce's general business model instead of reading the specific account record. It sees "Series B" and infers a company size that matches its general knowledge of Series B companies, not the actual data.

### Empty Field Interpretation

The agent treats empty fields as signals. No value in "last_contacted" becomes "the customer hasn't been contacted" (maybe nobody logged it). No value in "competitor" becomes "no competitive threat" (maybe nobody asked). No value in "budget" becomes "budget unknown — risk" (maybe the field isn't used for this record type).

Without data reading guides, every empty field is an opportunity for the agent to invent meaning.

### Stale Data Confidence

A field filled eight months ago on a record that's been through three status changes since. The agent reads it with the same confidence as yesterday's data. There's no mechanism in the model to distinguish fresh from stale — the data looks exactly the same in context.

A competitive positioning statement from Q1 treated as current in Q3. A pricing benchmark from a market that's moved 20%. A client preference from a product evaluation that ended months ago.

### Internal Identifier Display

The agent encounters an internal code — "STAGE_3_QUAL" or "CAT_ENT_02" — and presents it as if it's a meaningful label. Sometimes it guesses what it means based on the string. Sometimes it presents it raw. Neither is correct — these are system internals that need to be resolved to human-readable labels.

### Single-Layer Trust

The agent queries one data source, gets an answer, and presents it as fact. But the same information exists in three places — a structured field, a free-text note, and an activity log — and they disagree. The agent saw the first one it queried and never checked the others.

### Risk Language Creep

The agent finds data and frames it through a risk lens even when nobody asked for risk assessment.

"Last contact was 18 days ago" is a fact. "Gone 18 days without engagement — risk signal" is an interpretation. Same data. Very different framing. Without explicit rules about when risk language is appropriate, agents default to risk framing because analytical writing trains them to treat noting gaps as thorough.

### Over-Interpretation Cascade

The agent over-interprets one data point, which shifts the context for interpreting the next, which shifts the next, and so on. Each interpretation is slightly off. By the end of the analysis, the cumulative drift means the conclusion is technically connected to the original data but doesn't represent what the data actually says.

## The Common Thread

Every pattern shares the same root: the model has data, but doesn't have the operational knowledge to read it correctly. It applies general capability — pattern recognition, inference, synthesis — without the specific reading rules that would constrain those capabilities to produce accurate results.

Data reading guides prevent these patterns by making the operational rules explicit. Not as suggestions. At the same weight as safety instructions. Every violation produces output that looks authoritative but is wrong — and that's worse than producing nothing.
