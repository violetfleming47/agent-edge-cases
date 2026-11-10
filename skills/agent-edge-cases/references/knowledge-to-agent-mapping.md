# Knowledge-to-Agent Mapping

> How to map institutional knowledge to agents while controlling who sees what.

---

## The Mapping Principle

Every piece of institutional knowledge maps to specific agents. The mapping has two sides: which agents need this knowledge, and which agents must NOT have access to it.

The second side is as important as the first. A model with a risk assessment framework loaded will find risks. A model with a scoring rubric loaded will produce scores. The analytical lens creates the finding, not the other way around. If a validation agent loads audience profiles, it will evaluate audience fit — even though that judgment was already made upstream.

## Building the Matrix

Create a knowledge × agent matrix. Every cell is one of:

- **Loads** — this agent needs this knowledge to do its job
- **Inherits** — this agent receives the output of this knowledge (the decision, not the framework)
- **No access** — this agent must not see this knowledge

"No access" is the critical category. It's not enough for the agent to not need the knowledge — if it can access it, it will use it.

## What Form Knowledge Takes

Each piece of knowledge takes a form appropriate to its use:

**Reasoning frameworks** — loaded as reference documents. Teach the agent how to think about data. Applied at variable depth depending on mode (factual, diagnostic, research).

**Data reading guides** — loaded as reference documents. Teach the agent how to interact with systems. Applied consistently regardless of mode.

**Reference data** — loaded into a database. Queried by agents when needed. The agent gets specific records, not the full dataset.

**Skill rules** — embedded directly in the agent's scope definition. Procedural steps, noise-naming, prohibitions. Always active.

**Inherited decisions** — passed from upstream agents as structured output. The receiving agent gets the decision, not the data or framework that produced it.

## The Access Control Principle

A skill that can't access a framework can't misuse it. This isn't about trust — it's about architecture.

When you load a framework into an agent's context, you're giving it an analytical lens. The agent will look through that lens. If a reporting agent has a diagnostic framework loaded, it will produce diagnostics even when you asked for a report. If a generation agent has scoring rubrics loaded, it will second-guess the scoring that was already done upstream.

Access control means:
- Each agent loads the minimum frameworks for its judgment
- Everything else is structurally inaccessible
- Downstream agents receive distilled decisions, not raw framework data
- The loading rules are part of the skill definition, not a runtime decision

## Keeping It Current

Knowledge is not static. The mapping must specify who owns each piece and how it stays current:

- **Who authored it?** The domain expert whose reasoning it captures.
- **How often should it be reviewed?** Data reading guides when systems change. Reasoning frameworks when the business changes. Reference data on its own update cycle.
- **What triggers a review?** A system migration, a process change, a new data source, a learning system proposal, a trust incident caused by stale knowledge.
- **Who approves changes?** Framework changes are human-gated. The learning system can propose, but a human decides.
