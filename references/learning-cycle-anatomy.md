# Learning Cycle Anatomy

> The five components of a domain-specific learning cycle.

---

## 1. Observation Capture

What the agent notices, in what form, from what source.

The observation format must match the domain:

**Delta observations** — comparing two versions of the same thing. The AI's draft versus the human's published version. The agent's recommendation versus the human's decision. Structural, visible, contained. Works when there's a clear before and after.

**Signal observations** — detecting changes or patterns in ongoing data. A shift in client language, a change in engagement patterns, a new stakeholder appearing. Not comparing versions — assembling a picture from fragments. Works when data is continuous and evolving.

**Outcome observations** — tracking what happened after a decision. Did the recommended approach work? Did the audience respond as predicted? Did the evidence prove relevant? Works when outcomes are measurable and attributable.

Each type produces different raw material for pattern detection and requires different storage structures.

## 2. Decision Points

Where human judgment enters the cycle.

**Direct correction:** The human changes the output. The delta between original and corrected is a precise learning signal.

**Confirmation/denial:** The human confirms or denies the agent's observation. "Yes, that's right" or "no, that was a one-off." Different from direct correction because there's no specific fix — just a judgment call.

**Verbal direction:** The human provides qualitative guidance. "Too aggressive for this audience." "Lead with the data." Different from correction because the agent needs to interpret the guidance, not just apply a fix.

**Outcome review:** The human assesses whether the system's decision led to the desired outcome. Retrospective, not real-time.

Each type produces a different quality of learning signal. Direct corrections are the cleanest. Verbal direction is the richest but hardest to operationalise.

## 3. Pattern Detection

When observations accumulate into meaningful patterns.

**Grouping:** By what dimensions? Content learning groups by audience × format × topic × change type. Client intelligence groups by account × signal category × timeframe. The grouping must match the domain.

**Thresholds:** How many instances before a pattern is worth acting on? Too low and outliers trigger changes. Too high and real patterns are missed. Different domains need different thresholds: 3-5 for fast-moving editorial preferences, 5-10 for slower-moving client behaviour, 10+ for fundamental framework changes.

**Timeframe:** Over what period must the instances occur? Three similar observations in a week might be a pattern. Three over six months might be coincidence. The timeframe must match the domain's natural tempo.

**Confidence:** How confident is the pattern detection? Based on number of instances, consistency, recency, and absence of contradicting observations.

## 4. Upgrade Mechanism

What happens when a pattern is confirmed.

**Soft runtime adjustments (automatic):** Created when the pattern crosses the lower threshold. Weighted by confidence. Scoped to the specific context (not generalised). Decaying if not reinforced. Pipeline agents treat these as signals, not rules.

**Permanent framework changes (human-gated):** Proposed when the pattern sustains past the higher threshold over a longer timeframe. Includes full evidence trail. Human reviews, approves/modifies/rejects. Previous framework version preserved for rollback.

The distinction between these two speeds is the most important governance boundary in the learning system.

## 5. Decay

What happens to observations and patterns that aren't reinforced.

**Observation decay:** Individual observations age and eventually archive. The rate depends on the domain — editorial observations decay faster than structural patterns.

**Adjustment decay:** Soft adjustments that aren't reinforced by new observations lose confidence gradually. Below a threshold → archived. Superseded by a permanent framework change → archived immediately.

**Pattern decay:** Detected patterns that aren't confirmed by further observations lose significance. A pattern that was emerging but stopped appearing might have been seasonal, contextual, or coincidental.

Decay prevents the system from accumulating stale intelligence. Without it, every observation ever made continues to influence the system, even when the conditions that produced it no longer exist.
