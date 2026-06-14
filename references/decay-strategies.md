# Decay Strategies

> The four decay profiles with implementation guidance.

---

## Event-Driven Decay

**What it is:** Intelligence expires when a specific external event occurs, not on a calendar schedule.

**Best for:** Client relationships, strategic context, stakeholder maps, partnership status.

**How it works:** Define the change events that invalidate each type of intelligence. Monitor for those events. When one fires, flag all related intelligence for re-evaluation.

**Change events might include:** Leadership changes, organisational restructuring, strategy pivots, competitive displacement, contract renewal or expiration, M&A activity.

**Between events:** Intelligence stays fully active regardless of age. A client relationship insight from six months ago is still valid if nothing has changed.

**After an event:** Even intelligence captured yesterday might be stale. The event resets the clock, and previously valid intelligence needs re-evaluation.

## Velocity-Based Decay

**What it is:** Intelligence ages at a rate determined by how fast the domain moves.

**Best for:** Market signals, competitive intelligence, pricing benchmarks, technology landscape.

**How it works:** Define urgency tiers with different decay windows. Calibrate the windows to observed domain velocity.

**Typical tiers:**
- Time-sensitive: days (breaking news, urgent regulatory changes)
- Current: weeks (active market developments)
- Developing: months (emerging trends, multi-quarter shifts)
- Evergreen: 6+ months (structural patterns, permanent market features)
- Background: long-lived but low-weight (historical context)

**Active use extends freshness:** Intelligence that's been recently cited as evidence, confirmed by a human, or used in a successful output gets extended relevance. Active use is a reinforcement signal.

**Velocity itself adapts:** In a fast-moving market, decay windows should shorten. In a stable period, they can lengthen. The decay system should be able to recalibrate.

## Reinforcement-Based Decay

**What it is:** Intelligence stays active as long as it keeps being confirmed. Unconfirmed intelligence gradually loses influence.

**Best for:** Operational patterns, learned adjustments, behavioural observations, editorial preferences.

**How it works:** Track when each piece of intelligence was last reinforced. Apply confidence decay on a schedule. Below a threshold → archive.

**Typical schedule:**
- Not reinforced in 60 days → confidence reduced (e.g., by 0.15)
- Not reinforced in 90 days AND confidence below threshold (e.g., 0.3) → archived
- Superseded by a newer version → archived immediately

**Reinforcement signals:** The pattern is observed again, the intelligence is cited in a successful output, a human confirms it's still relevant, or a new observation is consistent with the pattern.

**Why not delete:** Archived patterns might become relevant again. A seasonal pattern that was dormant for months might resurface. Archive gives the system historical context without polluting active reasoning.

## Threshold-Based Decay

**What it is:** Intelligence is either fully current or immediately historical. No gradual aging.

**Best for:** Regulatory requirements, compliance rules, legal constraints, policy directives.

**How it works:** Define the external triggers that would invalidate the intelligence. Until a trigger fires, the intelligence is fully authoritative. After the trigger, it's immediately historical.

**Triggers might include:** A law changes, a regulatory ruling is issued, a company policy is updated, a standard is revised, a contract clause is modified.

**No gradual decay:** This is the key difference. Regulatory data doesn't "age." It's either the current law or it's not. The trigger is binary, and the transition is immediate.

**Monitor for triggers:** The system needs a mechanism to watch for trigger events — regulatory feeds, policy update notifications, legal alerts. Without monitoring, threshold-based intelligence stays active forever, even after the threshold has been crossed.
