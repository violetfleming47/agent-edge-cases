# Framework Depth Control

> How to design variable-depth framework application — the same expertise at different intensities for different purposes.

---

## The Principle

A framework is a textbook. How deeply you apply it depends on what you've been asked to do. A nurse taking vitals applies the medical textbook lightly — check the numbers, flag anomalies. A diagnostician applies it fully — differential diagnosis, hypothesis testing, treatment planning. Same textbook. Different depth.

Agents need the same variable depth. Without it, every query triggers the full analytical toolkit. Ask "what stage is this deal at?" and you get a risk assessment, a qualification audit, and three action items. The model applied its full capability because nobody told it to use less.

## Designing Modes

Each mode specifies:
1. **What frameworks are loaded** — some modes don't load certain frameworks at all
2. **What depth they're applied at** — vocabulary only, structure only, or full analytical application
3. **What output sections are available** — the structure constrains what the model can produce
4. **What language register is appropriate** — factual, analytical, diagnostic, advisory

### Factual Mode

Frameworks provide vocabulary and structure only. The agent knows what to call things and how to organise them. It does NOT apply scoring, risk assessment, gap analysis, or any analytical function.

**Loads:** Data reading guides (query correctly), structural vocabulary from reasoning frameworks (field names, categories)
**Does not load:** Scoring rubrics, risk assessment criteria, diagnostic frameworks, gap analysis tools
**Output sections:** Current state, recent activity, key people, next steps. No health scores. No risk indicators. No "Key Gaps."
**Language:** Descriptive. "Last contact was 18 days ago." Never "Gone 18 days without engagement — risk signal."

### Diagnostic Mode

Full framework application. Scoring, gap analysis, risk assessment, pattern detection, hypothesis formation.

**Loads:** Everything — data reading guides, reasoning frameworks at full depth
**Output sections:** All sections active including scoring, alignment checks, risk indicators, gap analysis, recommendations
**Language:** Analytical. Interpretations, assessments, confidence scores, hypotheses.

### Monitoring Mode

Targeted deviation detection. The agent checks for changes from established baselines, not a comprehensive assessment.

**Loads:** Baselines, change-detection subset of reasoning frameworks
**Does not load:** Full scoring rubrics, comprehensive diagnostic frameworks
**Output sections:** Changes detected, significance assessment, baseline comparison. No full assessment.
**Language:** Comparative. "This has changed since baseline" or "No significant changes detected."

### Research Mode

Deep investigation of a specific question or pattern. Only the framework sections relevant to the specific investigation are loaded.

**Loads:** Targeted framework sections relevant to the question
**Does not load:** Unrelated framework sections
**Output sections:** Investigation-specific. Focused findings, evidence assessment, hypothesis.
**Language:** Investigative. Evidence-based reasoning toward a specific question.

## Mode Selection

Two approaches, combinable:

**Explicit routing:** A routing layer classifies intent before the agent starts. The classification determines the mode. This is the cleanest approach — the agent never decides its own depth.

**Default conservative:** When intent is ambiguous, default to factual mode. Never default to diagnostic. If the user wants deeper analysis, they'll ask. This prevents the over-interpretation that happens when agents apply their full capability to simple questions.

## Output Structure as Enforcement

The output structure is the enforcement mechanism. If the template for factual mode doesn't have a "Risk Assessment" section, the model can't hallucinate a risk assessment. The structure constrains the model's tendency to apply capability that wasn't asked for.

This is more reliable than instructing the agent not to produce risk assessments. Instructions fight the model's drive to be helpful. Structure removes the space where the unwanted output would go.
