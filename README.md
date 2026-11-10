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

---

## Install

### Claude Code (as a plugin)

```
/plugin marketplace add violetfleming47/agent-edge-cases
/plugin install agent-edge-cases@agent-edge-cases
```

### Claude Code (manual copy)

```bash
git clone https://github.com/violetfleming47/agent-edge-cases.git
cp -R agent-edge-cases/skills/* ~/.claude/skills/
```

### Claude apps (claude.ai, Desktop)

Download a skill's `.zip` from the [latest release](https://github.com/violetfleming47/agent-edge-cases/releases/latest) and upload it under Skills in Claude's settings.

### Other harnesses (Cursor, Windsurf, custom agents)

Each `SKILL.md` is plain markdown. Load it as a rule or system prompt, and keep its `references/` folder alongside it.

### What's included

Every skill is a self-contained folder under `skills/`, with a `SKILL.md` and the reference documents it draws on:

- `agent-edge-cases`

---

## About

Created by [Violet Fleming](https://github.com/violetfleming47). These tools are grounded in a design philosophy developed across production multi-agent systems.

Part of a suite of open-source agent design tools:
- [Agent System Design](https://github.com/violetfleming47/agent-system-design) — design and decompose agent systems
- [Agent Knowledge Curator](https://github.com/violetfleming47/agent-knowledge-curator) — capture institutional knowledge
- [Agent Drift Prevention](https://github.com/violetfleming47/agent-drift-prevention) — prevent silent degradation
- **Agent Edge Cases** — failure modes you haven't considered
- [Agent System Review](https://github.com/violetfleming47/agent-system-review) — architectural review of existing systems

Licensed under [CC BY-NC 4.0](LICENSE).
