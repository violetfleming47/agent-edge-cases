# Institutional Knowledge Types

> The categories of knowledge that live outside structured data and determine whether agents process data or understand it.

---

## Tribal Knowledge

What everyone on the team knows but nobody documented. This is the most dangerous category because it's invisible — it only becomes apparent when someone who doesn't have it makes a mistake.

Examples:
- Customer relationship sensitivities ("Acme Corp is in a sensitive renegotiation — handle carefully")
- Process exceptions ("we never discount below 15% except for multi-year contracts")
- Data reliability ("that CRM field is unreliable because sales reps fill it in inconsistently")
- Interpretation shortcuts ("when a customer says 'we're evaluating options,' it means they already have a shortlist")
- Historical context ("we tried that approach with their industry last year and it backfired")

Tribal knowledge typically lives in experienced operators' heads. Making it machine-consumable is often the hardest and most valuable part of the knowledge capture process.

## Implicit Process Knowledge

The gap between the documented process and what people actually do. Every organisation has this gap — the formal methodology says one thing, but experienced operators have evolved shortcuts, workarounds, and judgment calls that the documentation doesn't capture.

Examples:
- Pricing: the difference between posted pricing and what actually gets approved
- Decisions: the difference between the org chart and how decisions actually get made
- Qualification: the methodology says seven steps, but experienced reps assess three key signals and know the answer
- Escalation: the documented escalation path versus who actually resolves things quickly

This knowledge matters because agents following the documented process will do technically correct things that experienced operators would never do.

## Interpretive Expertise

How experienced operators read the same data as juniors and see completely different things. This is the highest-value knowledge to capture because it's what transforms an agent from data retrieval to genuine reasoning.

Examples:
- Reading CRM notes: the senior sees four signals compressed into two sentences where the junior sees one update
- Interpreting engagement patterns: the senior knows a quiet period in context A means "stable" and in context B means "competitor conversation"
- Assessing data quality: the senior instinctively cross-references between data sources and knows which to trust when they conflict
- Recognising patterns: the senior spots a combination of signals that individually seem unremarkable but together indicate a significant shift

This expertise is the raw material for reasoning frameworks.

## Domain-Specific Semantics

What words and concepts mean in your specific context, which is often different from their general or industry meaning.

Examples:
- "Churn" in telecom (cancellation) versus SaaS (non-renewal) versus insurance (policy lapse)
- "Qualified lead" between sales teams at the same company
- "Stage 3" in your pipeline versus the industry standard definition
- "Enterprise" as a customer segment versus "Enterprise" as a product tier

Agents trained on general language will apply general meanings. Domain-specific semantics must be explicitly encoded, or the agent will confidently use the wrong definitions.

## Regulatory and Compliance Knowledge

Constraints that aren't in the data but must be respected in every output.

Examples:
- NDA boundaries (what information from which source can appear in which output)
- Compliance requirements (what claims require verification against authoritative sources)
- Legal constraints (what language is prohibited in customer-facing communications)
- Data handling rules (what information can be stored, shared, or combined)

This knowledge is often permanent until an external event changes it (a law, a ruling, a policy update). Until that trigger fires, the constraints are absolute.
