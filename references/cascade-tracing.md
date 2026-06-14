# Cascade Tracing

> Systematic approach to tracing change impact through an agentic system.

---

## The Process

### Step 1: Identify the Change

What specifically is changing? Be precise:
- Which framework, which section?
- Which data source, which field?
- Which agent, which output field?
- Which business rule, which aspect?

Vague change descriptions produce vague impact assessments. "We're updating the scoring framework" is too broad. "We're adding a new confidence dimension to the scoring framework's ICP assessment" is traceable.

### Step 2: Map Direct Dependents

Using the dependency graph, identify every component that directly depends on the changed component:
- Every agent that loads the changed framework
- Every agent that queries the changed data source
- Every agent that reads the changed agent's output
- Every framework that encodes the changed business rule

### Step 3: Assess Direct Impact

For each direct dependent, determine:
- **What assumption does this component make about the changed thing?**
- **Is that assumption still valid after the change?**
- **If not, what breaks or degrades?**

Categories:
- **Hard break:** The component expects something that no longer exists (a field, a category, a format)
- **Silent degradation:** The component still works but its reasoning is based on outdated assumptions
- **No impact:** The component doesn't use the changed aspect

### Step 4: Trace Indirect Impact

For each directly impacted component, repeat Step 2-3 with its dependents. Continue until you reach system edges.

The cascade often amplifies:
- A scoring framework change affects the scorer
- The scorer's output change affects the shaper, curator, and echo watcher
- Their output changes affect the prompt assembler
- The prompt assembler's output change affects the ghost writer
- The ghost writer's output change affects the validator
- The validator's output change affects the trust tracker

### Step 5: Check Historical Data

Does the change affect data already stored in the system?
- Learned adjustments that reference old categories → orphaned
- Baselines established under old assumptions → invalid
- Historical intelligence produced by the old version → still being read
- Audit trails that reference old framework versions → need version linking

### Step 6: Identify Silent Failures

The most dangerous cascade paths are the ones that don't produce errors:
- An agent receiving slightly different input but still producing output
- A framework category that was renamed but the old name still exists in stored data
- A threshold that shifted but the monitoring doesn't check that specific threshold
- A conflict resolution rule that covers the old format but not the new one

### Step 7: Plan the Change

Based on the impact assessment:
- **Atomic changes:** Update all affected components simultaneously. Use when the cascade is narrow and all changes are ready.
- **Incremental changes:** Update one layer at a time, verify, then update the next. Use when the cascade is wide or changes need validation.
- **Versioned changes:** Keep both old and new versions active during transition. Use when backward compatibility is needed temporarily.
- **Rollback plan:** For each stage, define what "reverting" looks like and whether it's possible.

## Common Blind Spots

- **Stored data referencing old versions.** Intelligence captured under the old framework doesn't automatically update when the framework changes.
- **Learning system lag.** Soft adjustments based on old patterns are still active. They may conflict with the new framework.
- **Cross-agent format assumptions.** Agent A changed its output, but the context assembly layer still expects the old format.
- **Lifecycle rules.** The decay rules reference categories or thresholds that changed. Stale data might not get cleaned up correctly under the new scheme.
