# Recalibration Patterns

> How to design systems that detect and correct their own drift.

---

## Scheduled Recalibration

The most straightforward approach: recalibrate on a regular schedule before drift accumulates.

**Baseline recalibration:** Periodically re-establish what "normal" looks like based on recent data. Monthly or quarterly, depending on domain velocity. The new baseline replaces the old one (old preserved as historical reference).

**Framework review:** Periodically assess whether frameworks still match the domain. Quarterly for fast-moving domains, semi-annually for stable ones. Check: are there new signal types? Have existing categories shifted? Are the interpretation rules still producing useful output?

**Threshold review:** Periodically check whether learning cycle thresholds are still appropriate. Are pattern detection thresholds catching real patterns? Are decay windows the right length? Is the learning tempo still matched to the domain?

## Signal-Driven Recalibration

Let the system's own signals tell you when recalibration is needed.

**Confidence distribution monitoring:** Track the distribution of confidence scores over time. If scores cluster unnaturally (all high, all medium), calibration has drifted. Trigger a recalibration review.

**Correction rate monitoring:** Track the rate of human corrections. A sustained increase suggests the system is drifting from the human's expectations. A sustained decrease might mean the system has improved — or that the human has stopped correcting and is just working around it.

**Learning signal monitoring:** Track the volume and character of learning observations. A spike in observations targeting the same framework area suggests that area needs review. A drought of observations for a framework that used to generate them suggests the framework has drifted enough that the learning system can no longer meaningfully compare against it.

**Output quality tracking:** If you have quality metrics (engagement, conversion, human satisfaction), track them over time. Gradual decline without a clear cause is the signature of system drift.

## Self-Analysis Cycles

Give agents the ability to assess their own performance over time.

Each agent that has a learning loop can run periodic self-analysis:
1. Pull its own observation history from the last period
2. Correlate its decisions with outcomes
3. Detect patterns in its own error rate or correction rate
4. Surface areas where its framework might need updating

This self-analysis doesn't change the agent's behaviour directly — it produces diagnostic intelligence that feeds into the human review process. The agent can notice it's drifting. Only the human can approve the correction.

## The Lifecycle Layer as Drift Prevention

The lifecycle layer — the daily cleanup process — is the first line of defence against drift from stale data. By expiring old signals, decaying unreinforced adjustments, and cleaning up orphaned records, it prevents the most common form of drift: agents reasoning against intelligence that no longer reflects reality.

Without the lifecycle layer, recalibration is reactive — you notice drift and fix it. With the lifecycle layer, the most common cause of drift is continuously addressed before it accumulates.

## Human Review as Recalibration

The human review process is itself a recalibration mechanism. Every time a human edits, redirects, or rejects agent output, the learning system captures a calibration signal. Over time, the accumulated corrections shift the system toward the human's current standards.

This works as long as the learning system is properly designed (domain-specific cycles, structural separation between observation and action, two-speed governance). Without proper learning architecture, human corrections either have no effect (not captured) or too much effect (single corrections causing system-wide changes).
