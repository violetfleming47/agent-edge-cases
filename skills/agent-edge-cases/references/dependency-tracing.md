# Dependency Tracing

> How to systematically trace dependencies across agents, frameworks, and data sources.

---

## The Four Dependency Types

### Framework Dependencies

Every agent loads frameworks — reasoning frameworks, data reading guides, or both. Each framework is a dependency. Map:

- Framework name → list of agents that load it
- Depth of application per agent (vocabulary only, structural, full analytical)
- Which sections each agent uses

An update to a framework section that only one agent uses has narrow impact. An update to a section that eight agents use has wide impact.

### Data Source Dependencies

Every agent that queries an external system depends on that system's schema, availability, and data quality. Map:

- Data source → list of agents that query it
- Which fields each agent reads
- Which fields are critical (agent fails without them) vs optional (agent degrades gracefully)
- What the agent assumes about the data (freshness, completeness, format)

### Decision Dependencies

Every agent that inherits an upstream decision depends on that decision's format, meaning, and reliability. Map:

- Producing agent → consuming agents
- What fields travel between them
- What the consuming agent assumes about the format and meaning of each field
- Whether the consuming agent would fail, degrade, or continue normally if a field changed

### Shared Store Dependencies

Shared intelligence stores (market signals, content insights, learned adjustments) are written by some agents and read by others. Map:

- Store → agents that write to it
- Store → agents that read from it
- What format readers expect
- What happens when the store is empty, stale, or formatted differently

## Building the Graph

For each agent, document:
1. What frameworks it loads (and which sections)
2. What data sources it queries (and which fields)
3. What upstream decisions it inherits (and which fields)
4. What shared stores it reads from
5. What it produces that others consume

Connect these into a directed graph. Edges represent dependencies. The direction shows who depends on whom. Weight edges by criticality: required dependencies vs optional ones.

## Reading the Graph

- **High fan-out nodes** — a component with many dependents. Changes here cascade widely. These need the most careful change management.
- **Long chains** — dependencies that span many layers. Changes at the start propagate unpredictably to the end.
- **Cycles** — agent A depends on a store that agent B writes to, and agent B depends on a store that agent A writes to. Not necessarily wrong, but requires careful ordering.
- **Orphans** — agents loading frameworks they don't use, or reading from stores that are empty. Candidates for cleanup.
