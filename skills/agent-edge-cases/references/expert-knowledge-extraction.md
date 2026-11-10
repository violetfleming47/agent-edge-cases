# Expert Knowledge Extraction

> How to extract the interpretive lens from domain experts and structure it for agents.

---

## The Challenge

The knowledge you need lives in your best people's heads. Not as a document they can hand over — as an interpretive lens they apply automatically, often without being aware they're doing it. The senior account manager doesn't think "I'm now applying my stakeholder composition analysis framework." They just see the data and notice things.

Making this implicit expertise explicit is the hardest part of knowledge capture. The expert can't always articulate what they do. They just "know." Your job is to help them unpack that knowing.

## Extraction Approaches

### Work Through Real Examples

Don't ask "how do you evaluate accounts?" in the abstract. Put real data in front of the expert and ask them to think out loud.

"Here's a CRM record. What do you notice? What concerns you? What seems fine? What would you look at next?"

Watch for:
- **What they look at first.** This reveals their priority hierarchy.
- **What they skip.** This reveals what they've learned is noise.
- **What they cross-reference.** This reveals which data layers they trust and which they verify.
- **Where they pause.** This reveals where interpretation is required — the data doesn't speak for itself.
- **What they infer.** This reveals the patterns they've learned to recognise.

### Compare Junior vs Senior Readings

Show the same data to a junior and a senior operator. The differences in their observations reveal the interpretive expertise the senior has accumulated:

- The junior reports what the data says. The senior reports what it means.
- The junior sees one signal. The senior sees four compressed into the same note.
- The junior takes the data at face value. The senior checks freshness, cross-references, and adjusts for context.
- The junior treats all data equally. The senior weights by source reliability and recency.

Those differences are the framework. Document them.

### Capture Corrections

When a senior operator corrects an agent's output or a junior's analysis, the correction is a direct signal:

- What did the agent/junior get wrong?
- Why is the correction right?
- What interpretive rule was the agent/junior missing?

Each correction is an observation. Patterns of corrections across multiple instances reveal the framework rules that need to be encoded.

### Ask About Edge Cases

Standard cases don't reveal much — the junior gets them right too. Ask about the hard ones:

- "When do you override the standard methodology?"
- "What makes you doubt the data?"
- "When do you escalate instead of proceeding?"
- "What signals make you worried even when the numbers look fine?"
- "When is absence of information actually informative?"

These edge cases are where the expert's judgment framework lives — the rules that handle the 20% of situations that account for 80% of the value.

## Structuring What You Extract

Raw expert knowledge needs to be structured into framework components:

- **Priority observations** → signal taxonomy (what types of signals exist and what each means)
- **Cross-referencing habits** → data reading guide rules (what to trust, what to verify)
- **Interpretation patterns** → reasoning rules (how to read messy data, how to decompose notes)
- **Confidence instincts** → calibration criteria (what constitutes high, medium, low confidence)
- **Edge case handling** → uncertainty guidance (how to express partial knowledge)
- **Correction patterns** → interpretation rules (what the agent keeps getting wrong)

## Validation

Once structured, validate the framework with the expert:

- "Does this capture how you think about it?"
- "What's missing?"
- "Where would this framework get it wrong?"
- "What situations wouldn't this handle?"

Then validate with data: run the framework against historical examples where the expert's judgment is known. Does the framework produce assessments that align with what the expert concluded? Where they diverge, the framework needs refinement.

The framework will never be perfect on day one. That's what learning cycles are for — the framework evolves through accumulated observations and human corrections over time.
