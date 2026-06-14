# Data Freshness Architecture

> How to build decay metadata into the data model so agents know how much to trust what they read.

---

## Decay as Design-Time Decision

Every piece of intelligence your system captures should have a decay profile defined at the point of capture, not retroactively. When an agent captures a competitive signal, the system should know: what kind of signal is this? What's its expected shelf life? What events would invalidate it? What reinforcement would extend it?

## Decay Metadata Fields

Each intelligence record carries:

**decay_type** — calendar, event-driven, velocity-based, reinforcement-based, or threshold-based. Determines which decay rules apply.

**decay_triggers** — what would make this stale. For event-driven: the specific events. For velocity-based: the urgency tier. For reinforcement-based: the reinforcement conditions. For threshold-based: the external triggers.

**confidence_at_capture** — how reliable was this when the agent captured it? Not all intelligence starts at 100%. A signal from a single source starts lower than one corroborated across three sources.

**last_reinforced** — when was this last confirmed, cited, or actively used. Reinforcement extends relevance. This timestamp is the anchor for reinforcement-based decay.

**freshness_window** — the expected duration of relevance based on decay type and urgency. Used to calculate current freshness status.

**status** — active, aging, archived, expired. Managed by the lifecycle system.

## Freshness-Aware Querying

When agents query the knowledge store, they don't just get the intelligence — they get its freshness profile. The reasoning framework teaches the agent how to weight data based on freshness:

- **Active:** Full confidence. Recently captured or reinforced.
- **Aging:** Reduced confidence. Approaching freshness window boundary. The agent includes a freshness note: "This was captured X ago — consider whether it's still current."
- **Archived:** Not in active queries by default. Available for historical analysis if explicitly requested. Never treated as current intelligence.
- **Expired:** Removed from queryable stores. Available only in archive.

## The Lifecycle Layer

A dedicated lifecycle process runs before all other agents — the first thing every day. It:

1. Checks freshness windows across all intelligence tables
2. Applies decay rules: ages what's approaching the boundary, archives what's past it
3. Applies reinforcement decay: reduces confidence on unreinforced intelligence
4. Extends freshness on recently reinforced intelligence
5. Checks threshold triggers for regulatory/compliance data
6. Logs all actions taken

By the time other agents start their work, the intelligence layer has been cleaned. They're reasoning against current data, not a mix of current and historical.

## The Archive Boundary

Archived data never re-enters the active store without explicit re-validation. This is a one-way wall:

- Agents can reference archived data for historical context
- Agents can compare current data against archived data to detect trends
- Agents cannot treat archived data as current intelligence
- Re-activation requires human approval or a formal validation process

Without this boundary, stale intelligence quietly re-enters active reasoning — an agent pulls an old record for comparison and then factors it into its current assessment.
