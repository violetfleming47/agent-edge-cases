# Output Structure by Mode

> How output structures enforce mode boundaries — the shape of the output constrains what the model can produce.

---

## Structure as Constraint

Output structures are not formatting templates. They're mode enforcement. When the structure for a factual briefing doesn't include a "Key Risks" section, the model can't hallucinate risks into a factual update. The structure removes the space where unwanted output would go.

This is more reliable than instructions. "Don't produce risk assessments in factual mode" fights the model's drive to be comprehensive. A structure that simply doesn't have a risk section makes it structurally impossible.

## Mode-Gated Sections

The same underlying report might exist in multiple modes. The sections that appear depend on the mode:

### Factual Mode
```
## Current State
[Status, stage, key metrics — descriptive only]

## Recent Activity
[Last 30 days of interactions, changes, events — chronological, factual]

## Key People
[Who's involved, their roles — no assessment of engagement quality]

## What's Next
[Scheduled events, pending actions — factual, not prescriptive]
```

No health score. No scoring table. No risk indicators. No gap analysis. No recommendations.

### Diagnostic Mode
```
## Assessment Summary
[Overall health score, key findings, confidence level]

## Scoring
[Per-dimension scores against framework criteria]

## Alignment Analysis
[Current state vs expected state, gaps identified]

## Risk Indicators
[Signals that warrant attention, with severity and confidence]

## Pattern Analysis
[Trends, changes from baseline, hypothesis formation]

## Recommendations
[Specific next actions with priority and rationale]
```

The same data drives both. The mode determines which analytical lenses are applied and which sections appear.

## Risk Language Control

The most common mode violation: risk language creeping into factual contexts.

**Factual:** "Last contact was 18 days ago. The next scheduled meeting is July 15."

**Diagnostic:** "Contact frequency has declined 40% from the account baseline (weekly → biweekly). Combined with a stakeholder shift from VP to Director level in the last two meetings, this may indicate deprioritisation. Confidence: 55%."

Both are valid. Both use the same data. But the factual version in a diagnostic report would be too thin, and the diagnostic version in a factual report would be over-interpretation.

The output structure ensures the right version appears in the right context by making it structurally impossible to produce the wrong one.

## Section Dependencies

Some sections should only appear if certain conditions are met:

- "Pattern Analysis" only appears if baselines exist for this context
- "Competitive Assessment" only appears if competitive data was found
- "Gap Analysis" only appears if the scoring revealed gaps above a significance threshold

Conditional sections prevent the model from producing empty-but-present sections that it fills with speculation. If there are no gaps worth mentioning, the gap section shouldn't exist — not exist-but-say "no significant gaps found."
