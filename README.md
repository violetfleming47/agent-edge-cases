# Agent Edge Cases

> Everything you haven't considered in your agent design.

---

## What This Package Does

This isn't a diagnostic tool. It's a perspective shift.

Most agent systems fail not because something breaks, but because the design never accounted for what would happen when the agent hit real data, real ambiguity, and real complexity. The output looks fine. It passes every quality check. It's just not precise — and nobody can name why.

This is a single skill that walks you through the failure modes most people building agents have never thought about. Each one is drawn from real patterns observed in production multi-agent systems. Some will apply to your system. Some won't. The ones that make you uncomfortable are the ones worth paying attention to.

---

## What It Covers

- **Cross-pollination** — your monolith is finding coherence across perspectives instead of preserving the tensions that are the actual information
- **Vacuum filling** — you left room in the reasoning space and the agent filled it with capability nobody asked for
- **Mushy output** — every decision was made with approximate inputs and the result passes quality checks but has no precision
- **Silent re-interpretation** — each agent slightly reinterprets the upstream decision until the output addresses a different reality at every level
- **Absence-as-signal traps** — the agent is treating every empty field as a finding
- **Single-observation reactions** — your learning system is changing behaviour based on one atypical edit
- **Framework contamination** — an agent with a framework it doesn't need is using it
- **Silent data aging** — intelligence from months ago is treated with the same confidence as yesterday's
- **Wrong human placement** — humans at every checkpoint, or no humans at all
- **Symmetric trust boundaries** — the system can escalate its own authority as easily as it de-escalates

---

## How to Use This

Describe your agent system or just ask to see the failure modes. Each one stands alone as a concept worth understanding.

If something makes you uncomfortable, the other packages help you fix it:
- **Agent System Design** for decomposition and scope problems
- **Agent Knowledge Curator** for knowledge and interpretation problems
- **Agent Drift Prevention** for decay, drift, and cascade problems
- **Agent System Review** for a full diagnosis of an existing system
