# Interpretation and Confidence

> Confidence calibration, freshness rules, and absence-as-signal guidance.

---

## Confidence Is Not Hedging

"It seems like the customer might be considering alternatives" is not a confidence statement. It's hedging — vague uncertainty that tells the reader nothing about how uncertain or why.

Confidence is structured: what was observed, what was inferred, how many data points support the conclusion, how recent they are, and what would change the assessment.

"Three interactions over two months show a shift from strategic to operational language. Combined with a new procurement stakeholder appearing in the last call, this pattern is consistent with vendor re-evaluation. Confidence: 65%. Supporting: language shift, stakeholder change. Conflicting: deal velocity hasn't slowed."

That's useful. The reader knows exactly what the agent saw, what it concluded, and why it's not fully certain.

## Calibration Criteria

Confidence should be expressed as a percentage or a calibrated label. Calibration means the labels have defined, consistent meaning:

**High confidence (80-100%):** Multiple corroborating signals. Recent data. Direct observation or primary sources. The conclusion would surprise no experienced operator.

**Medium confidence (50-79%):** Some evidence but gaps exist. Signals point in a direction without conclusive proof. Some inference is involved. An experienced operator might agree or might want more data before committing.

**Low confidence (20-49%):** Single data points, aged data, indirect inference, or conflicting signals. This is a hypothesis, not a conclusion. Useful as a starting point for investigation, not for decision-making.

**Insufficient (<20%):** Not enough information to form even a hypothesis. The agent states what it observed and what would be needed to assess further. This is a valid output — better than a forced low-confidence guess.

## Freshness Rules

Not all data ages at the same rate. Freshness thresholds should be defined per data type:

- **Competitive pricing** — stale in weeks. Markets move.
- **Client priorities** — variable. Stable for the duration of a project, but can shift after a leadership change or strategic pivot.
- **Regulatory constraints** — effectively permanent until an external event changes them.
- **Contact information** — stable for years in some domains, months in others.
- **Market signals** — depends on urgency classification. Time-sensitive signals expire in days. Developing trends hold for months.
- **Operational metrics** — current quarter is relevant. Last quarter is context. Older is historical.

When data is within its freshness window: use at full weight.
When approaching the edge: flag with a freshness note.
When past the window: treat as historical context, not current intelligence. "This was captured [timeframe] ago — treat with appropriate caution."

## Absence-as-Signal

The most dangerous reasoning pattern. When the model interprets what's NOT in the data as meaningful.

### When Absence IS a Signal

In diagnostic or analytical contexts, absence can be meaningful:
- No executive engagement after three months of an enterprise deal → potential risk
- No competitive mention in any recent call transcript → either no competition or the customer isn't sharing
- No activity for 30 days on a previously active account → pattern change worth investigating

### When Absence IS NOT a Signal

In factual or reporting contexts, absence is just empty data:
- No value in "last_contacted" → nobody logged it, not "no contact occurred"
- No value in "budget" → field wasn't filled in, not "no budget exists"
- No competitor listed → nobody entered one, not "no competitive threat"

### The Rule

Absence-as-signal reasoning is only permitted when:
1. The context is explicitly diagnostic or analytical
2. The specific field is one where absence has been defined as potentially meaningful
3. The agent expresses the interpretation with appropriate uncertainty
4. The agent also states the alternative explanation (data wasn't captured)

Default: absence means "we don't know." Not "doesn't apply." Not a negative finding.
