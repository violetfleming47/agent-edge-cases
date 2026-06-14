# Data Reading Guide Structure

> The anatomy of a well-structured data reading guide — operational rules for getting accurate data and avoiding quiet hallucinations.

---

## What a Data Reading Guide Is

Operational rules for interacting with your actual systems. Not interpretation (that's reasoning frameworks) — mechanics. How to query correctly. What to trust. What to cross-reference. What the data architecture looks like underneath.

Data reading guides come from knowing the system — its quirks, its limitations, its field-level reliability. They change when the data architecture changes: new fields, new APIs, new systems integrated, old fields deprecated.

## The Components

### 1. System Overview

What this data source is, how it's structured, and what the agent needs to know before querying:

- What kind of system it is (CRM, ERP, data warehouse, API)
- How data is organised (tables/entities, relationships, hierarchy)
- What the primary keys and linking fields are
- What the update patterns look like (real-time, batch, manual)

### 2. Query Rules

The mechanics of getting correct data:

- **Never infer what you didn't pull.** If a property wasn't in your query, you don't have it. Don't guess based on a name or general knowledge. Models do this constantly — they recognise something and start filling in details from training data instead of the actual record.
- **Handle pagination.** Does this API return all results or paginated sets? What's the default page size? Always check whether you have the full dataset. Never assume a single call returned everything.
- **Respect filter limits.** What scoping is required before queries return meaningful results?
- **Use known query patterns.** Document the specific query shapes that are known to return correct results. The agent uses these rather than constructing queries from scratch.

### 3. Field Trust Hierarchy

Which fields to trust and which to verify:

**Tier 1 — System-managed fields:** Timestamps, auto-calculated values, workflow-generated statuses. Generally reliable but check if the inputs are current.

**Tier 2 — Structured human input:** Dropdowns, categorised fields, standardised entries. Reliable within the constraints of the options available, but humans sometimes pick the closest option rather than the right one.

**Tier 3 — Free-text human input:** Notes, descriptions, custom fields. Entered by humans with varying discipline, varying terminology, and varying completeness. Must be interpreted, not quoted. Cross-reference against structured fields when possible.

**Tier 4 — Derived or calculated fields:** Values computed from other fields. Only as good as the source fields and the calculation logic. Verify the freshness of inputs.

### 4. Empty Field Interpretation

The golden rule: **always distinguish empty from missing.**

- **Null/empty** — the field exists but has no value. Could mean: nobody filled it in, it was never relevant, it was relevant but not captured, or it was deliberately left blank.
- **Field absent** — the field doesn't exist on this record type. Different from empty — it's structurally not applicable.
- **Default value** — the system populated a default. The human may or may not have consciously confirmed it.

Default interpretation when context is ambiguous: "we don't know" — never "doesn't apply" or "negative." Absence is not evidence.

### 5. Cross-Reference Rules

When the same information exists in multiple places:

- **Define the hierarchy.** Which source is authoritative when they conflict?
- **Present conflicts.** When two sources disagree, show both. Don't quietly pick whichever supports the narrative.
- **Check recency.** The more recently updated source is more likely current — but not always. A manual note from yesterday might reflect reality better than a structured field updated by a batch process last night.

### 6. Identifier Resolution

- **Never display raw internal identifiers.** Stage IDs, category codes, status integers — these are system internals that look plausible as labels but mean something different from what they appear to say.
- **Resolve or flag.** Look up the human-readable label. If resolution fails, say so: "I can't resolve identifier X-2847" — never display it as if it's meaningful.
- **Context-dependent identifiers.** Some codes mean different things in different contexts (e.g., a stage label that changes meaning based on which pipeline the record is in). Scope before interpreting.

### 7. Freshness Rules

- **Check timestamps.** When was this record last updated? When was this specific field last modified?
- **Define freshness thresholds.** Per field type, how old is too old? This varies: a contact's email is stable for years. A deal's next steps might be stale in a week.
- **Flag staleness.** Don't silently present aged data as current. State when it was captured and let the downstream agent or human factor in the age.
