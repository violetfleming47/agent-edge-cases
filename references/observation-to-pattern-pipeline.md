# Observation-to-Pattern Pipeline

> Structural separation between observation and action — why it must be architectural, not aspirational.

---

## The Principle

A single observation is not a pattern. Two observations are not a pattern. If a learning agent can act on a single observation, one atypical instance ripples through the entire system.

The separation between observation and action must be structural. The observing agent literally cannot write to the frameworks. It writes to an observation store. A separate process reads that store on its own cycle. Only that process can propose changes. Only a human can approve permanent changes.

## The Pipeline

### Stage 1: Observe (Per Event, Immediate)

An event triggers observation: a human edits a draft, a signal is confirmed or denied, an outcome is measured.

The observing agent produces a structured observation:
- What happened
- The agent's interpretation of what happened
- The context (who, what, when, which domain, which framework was active)
- Confidence in the interpretation

The observation is written to the observation store. No system changes. Pure recording.

### Stage 2: Accumulate (Continuous, Passive)

Observations accumulate in the store. They're linked to their contexts, timestamped, and tagged with the framework version that was active when they were produced.

No analysis happens at this stage. The observations are raw material waiting for the next cycle.

### Stage 3: Detect (Cyclic)

A pattern-detection process runs on a defined schedule — daily, weekly, or monthly depending on the domain. It reads the observation store and looks for patterns:

- Groups observations by context dimensions
- Checks whether any group crosses the pattern threshold
- Assesses the confidence of detected patterns
- Checks for contradicting observations

This process has read access to the observation store and write access to the adjustment/proposal store. It does NOT have write access to frameworks.

### Stage 4: Adjust (Automatic, Bounded)

When a pattern crosses the lower threshold, the detection process creates a soft runtime adjustment:
- Scoped to the specific context
- Weighted by confidence
- Tagged with the observations that produced it
- Subject to decay if not reinforced

Pipeline agents read these adjustments as weighted signals. They factor them in but don't treat them as hard rules.

### Stage 5: Propose (Human-Gated)

When a pattern sustains past the higher threshold over a longer timeframe, the detection process writes a proposal to the staging queue:
- The pattern and its evidence
- The specific framework change recommended
- The impact assessment (which agents would be affected)
- The provenance trail back to individual observations

This sits in the queue until a human reviews it. The human decides: approve, modify, or reject.

### Stage 6: Evolve (Human-Approved)

If approved, the framework is updated:
- New version created (previous version preserved)
- Corresponding soft adjustments archived (the permanent change supersedes them)
- Audit trail complete: framework change → proposal → pattern → observations → original events

## Why Structure Matters

Aspirational separation ("the agent should observe but not act") fails under pressure. The model's drive to be helpful pushes it to act on what it observes. The data is right there. The correction is obvious. Why wait?

Structural separation makes acting impossible. The observing agent has no write access to the things it would want to change. The pattern-detection process has no awareness of individual observations' urgency. The human gate on permanent changes ensures that the system's reasoning structure only evolves when a human has examined the evidence and made a deliberate decision.

Three things this produces:
1. **No knee-jerk reactions.** A single atypical edit can never change the system.
2. **Evidence accumulation.** The system must prove a pattern exists before changing behaviour.
3. **Complete audit trail.** Every framework change traces back through patterns, observations, and original events.
