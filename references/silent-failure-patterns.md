# Silent Failure Patterns

> How cascades manifest as degradation rather than breakage — the failures nobody catches until they compound.

---

## Why Silent Failures Are Worse

Hard failures are visible. An agent crashes, an API returns an error, a field is missing and the pipeline stops. Someone notices. Someone fixes it.

Silent failures produce output. The agent runs. The pipeline completes. The result looks reasonable. But the reasoning was based on outdated assumptions, stale data, or mismatched formats — and the output is subtly wrong in ways that pass every quality check.

One subtly wrong output is fine. Thirty subtly wrong outputs, and the system has lost precision without anyone noticing. This is the failure mode that degrades trust — not a dramatic collapse, but a slow realisation that "the output just doesn't feel right anymore."

## The Patterns

### Format Mismatch

An upstream agent changed its output format. The downstream agent still runs — it doesn't crash because the field exists and contains data. But the data means something slightly different now.

Example: The scoring agent added a new confidence dimension. The prompt assembler still reads the confidence field but interprets it as the old single-dimension score. The brief it produces uses the wrong confidence level. The ghost writer writes with the wrong level of conviction. The output is slightly off, but nobody can point to why.

### Orphaned References

A framework category was renamed or removed. But learned adjustments, baselines, and historical data still reference the old name. The lifecycle system doesn't clean them up because it checks timestamps, not category validity.

Example: "Gatekeeper" ICP was renamed to "Risk Manager." Fourteen learned adjustments still target "Gatekeeper." They're never matched, so the scoring agent doesn't apply them. The refinements that took months to learn are silently lost.

### Stale Calibration

Confidence thresholds, quality scores, or significance levels were calibrated under old conditions. The conditions changed but the thresholds didn't.

Example: The validator's auto-approve threshold of 85 was set when the system was producing simpler content. Content complexity increased, and 85 now represents lower relative quality. More content auto-approves than should, but each individual piece technically meets the threshold.

### Baseline Erosion

Baselines were established during a stable period. The domain shifted gradually, and the baseline absorbed the shift instead of flagging it. Now the baseline represents the new normal, and the monitoring agent can't detect deviations from what was actually the intended standard.

Example: Content targeting drifted over three months from specific ICP personas to general audience. Each week's output was within the baseline tolerance. The baseline adjusted. The monitoring agent never flagged it. Three months later, the content is generic but the system says it's on target.

### Cross-Layer Contamination

A change in one layer unexpectedly affects another because of an undocumented dependency.

Example: The lifecycle agent adjusted its decay schedule — signals now expire after 14 days instead of 7. The researcher, running at 8 AM, now sees more signals. The suggester, running at 9 AM, generates more suggestions. The calendar fills up. The human reviews more items. Review quality drops because of volume. Output quality drops. Nobody connects it back to the decay schedule change.

## Detection

Silent failures are detected through:
- **Output quality trending** — track quality metrics over time, look for gradual decline
- **Correction rate trending** — track human correction rates, look for sustained increases
- **A/B comparison** — periodically compare agent output against expert human judgment
- **Provenance auditing** — trace a sample of outputs back through the full pipeline, checking each step
- **Framework-reality comparison** — periodically check whether framework categories and rules still match the actual domain

None of these are automatic. Silent failures require active vigilance — which is why they're the failure mode that catches teams who built the system and then stopped watching it.
