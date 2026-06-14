# Drift Indicators

> Symptoms that indicate different types of drift in an agentic system.

---

## Framework Drift Indicators

The frameworks no longer match the domain they describe.

**Symptoms:**
- Agent outputs are technically correct but feel increasingly irrelevant
- New categories of data appear that agents don't know how to classify
- Confidence scores cluster unnaturally (all high or all medium — the calibration is off)
- Human corrections increasingly target interpretation, not mechanics
- The learning system proposes framework changes more frequently (the adjustments are compensating for outdated frameworks)

**Root cause:** The domain evolved but the frameworks stayed static. New signal types, new patterns, new priorities that the framework doesn't account for.

## Baseline Drift Indicators

The reference points for "normal" no longer represent reality.

**Symptoms:**
- The monitoring agent either flags everything (old baseline, everything looks anomalous) or flags nothing (baseline absorbed the new normal, real anomalies blend in)
- Trend detection produces obviously wrong conclusions
- Pattern significance assessments are miscalibrated
- Historical comparisons produce misleading results

**Root cause:** The baseline was established under conditions that have since changed. Seasonal shifts, market changes, growth, contraction — the reference point is stale.

## Scope Drift Indicators

Agents encountering data or situations their scope definition didn't anticipate.

**Symptoms:**
- Agents absorbing adjacent data into their outputs (noise that wasn't named)
- New adjacent functions appearing that aren't covered by prohibitions
- Agents producing output types that weren't in their original specification
- Edge cases increasing in frequency (what was edge is now mainstream)

**Root cause:** The data landscape changed. New data sources, new fields, new adjacent systems that the original scope definition didn't account for.

## Composition Drift Indicators

The inheritance chain between agents breaking down.

**Symptoms:**
- Downstream agents receiving outputs they can't interpret correctly
- Conflict resolution rules encountering conflicts they weren't designed for
- The synthesis layer producing garbled or incomplete briefs
- Subtle inconsistencies between what an upstream agent decided and what the downstream agent acted on

**Root cause:** Agents evolved independently. An upstream agent changed its output format, added new fields, or shifted the meaning of existing fields without the downstream agents being updated to match.

## Learning Drift Indicators

The learning system itself becoming miscalibrated.

**Symptoms:**
- Soft adjustments accumulating without improving output quality
- Framework change proposals that seem obvious (should have been caught earlier)
- A new human reviewer causing rapid adjustment churn (the system is overfitting to one person)
- Pattern detection triggering on noise (thresholds too low) or missing real patterns (thresholds too high)

**Root cause:** The learning cycle's parameters (thresholds, tempos, decay schedules) were calibrated for conditions that have changed. Or the source of learning signal has shifted (different reviewer, different criteria, different standards).

## The Meta-Indicator

The most reliable indicator that drift is occurring: **the output just doesn't feel right anymore, but nobody can name why.**

The agents aren't failing. The outputs aren't wrong in any obvious way. The quality checks pass. But the results feel off — slightly disconnected from reality, slightly less useful than they were, slightly generic where they used to be specific.

This is what drift looks like from the outside. Every individual output is defensible. The aggregate is slowly losing precision. And because each individual piece passes inspection, nobody catches it until the cumulative drift is significant.
