---
name: agent-edge-cases
description: Walk through ten failure modes most agent builders never consider — cross-pollination, vacuum filling, mushy output, silent re-interpretation, absence-as-signal traps, silent data aging and more. Use when designing an agent system or sanity-checking one for blind spots.
---

# Agent Edge Cases

> Everything you haven't considered in your agent design. Not an audit of a specific system — a walk through the failure modes you don't know exist.

---

## What This Skill Does

This isn't a diagnostic tool. It's a perspective shift.

Most agent systems fail not because something breaks, but because the design never accounted for what would happen when the agent hit real data, real ambiguity, and real complexity. The output looks fine. It passes every quality check. It's well-structured, confident, and completely plausible. It's just not precise — and nobody can name why.

The reason nobody can name it is that these failure modes are architectural, not operational. They don't produce errors. They produce subtly wrong output that looks subtly right. The agent isn't malfunctioning — it's doing exactly what it was designed to do. The design just didn't account for how models actually behave when they encounter the situations your agents will encounter every day in production.

This skill walks you through those failure modes. Each one is drawn from real patterns observed in production multi-agent systems — not theoretical risks, but things that actually happen when agents hit real data at scale. Some will apply to your system. Some won't. The ones that make you uncomfortable are the ones worth paying attention to.

---

## How to Use This

Describe your agent system — what it does, how it's structured, what agents exist, how they connect. Or just describe what you're building, even if it's early. I'll walk you through what you might not have considered.

You can also use this without a specific system. Just ask to see the failure modes. Each one stands alone as a concept worth understanding before you build.

---

## The Edge Cases

### 1. Your Monolith Is Cross-Pollinating

You built one agent that handles multiple aspects of a decision. It scores the audience, selects the format, picks the evidence, and generates the output. The result looks comprehensive — every section supports every other section. The conclusions feel integrated and coherent.

That's the problem. In reality, those dimensions often point in different directions. The audience data should create tension with the evidence availability. The format constraints should push back against the content direction. When everything agrees perfectly, the model found coherence — it rationalised rather than analysed. It smoothed the tensions away, and the tensions were the actual information.

This is what cross-pollination looks like. The model holding all the analytical perspectives in one context window doesn't keep them separate. It finds the story that makes them all agree. The audience assessment influences the format choice. The format choice influences the evidence selection. The evidence selection confirms the audience assessment. Everything supports everything — and the output is an internally consistent fiction rather than an honest assessment of competing factors.

Separate the judgments. Let each one produce its assessment independently. The tensions between them — the places where audience, evidence, format, and strategy don't agree — are where the most important decisions live.

**The question:** Are any of your agents holding multiple analytical perspectives in a single context window? Are the conclusions integrated because the analysis genuinely converged, or because the model made them converge?

### 2. You Left a Vacuum

You told the agent what to do. You gave it a clear task description, good data access, maybe some guidelines. But you didn't fill its reasoning space with enough framework to keep it occupied. So it filled the vacuum with capability.

The scoring agent started commenting on pipeline health because it could see CRM data. The validation agent started rewriting content because it had access to the draft. The evidence agent started reshaping the argument because it seemed helpful. None of these are malfunctions. They're what models do when you leave a vacuum in their reasoning space. The model saw data, had the ability to do something with it, and nobody said not to.

Prohibitions alone won't fix this — "don't do X" is fighting the model's drive to be helpful. The model can see the data. It has the capability. Telling it not to use that capability is aspirational. It works sometimes. It fails when the data is compelling, when the opportunity is obvious, when the model is trying to produce the most comprehensive response it can.

The fix is filling the space so completely that there's nowhere to wander. Not by adding rules — by adding depth. Give the agent enough framework for its actual job that it's too busy doing what it should be doing to improvise. A scoring agent with a deep, detailed qualification framework, specific decomposition rules, and explicit confidence calibration doesn't have time to comment on pipeline health. Its reasoning space is full.

**The question:** For each agent, is the reasoning space filled with enough framework that the agent is too busy doing its job to improvise? Or are there gaps — areas where the agent encounters data and has to decide what to do with it on its own?

### 3. Your Output Is Mushy

Your system produces output that passes every quality check. It's well-written, addresses an audience, includes evidence, matches a format. The only thing wrong is that none of those decisions was made with precision.

The audience targeting is approximate. "This seems like it's for mid-market tech companies" rather than a specific, scored audience match. The evidence selection is convenient rather than deliberate — the agent used what was readily available, not what best supported the argument. The format is whatever the model felt like producing rather than a conscious choice based on audience and channel constraints.

Every edge is soft. One mushy piece is fine — nobody notices. Thirty mushy pieces and the system has no identity. The voice drifts between pieces. The targeting is inconsistent across outputs. The format distribution is random. The system produces volume without precision, and the volume itself masks the lack of precision because each individual output passes inspection.

The cause is almost always that multiple judgments are being made in a single context window, where they influence each other instead of being made independently. The audience assessment leaks into the format choice. The format choice leaks into the evidence selection. Everything is slightly shaped by everything else, and the result is output where every decision is approximately right and precisely nothing.

**The question:** Is each judgment in your system made independently, with clean inputs, by an agent whose only job is that judgment? Or are they all influencing each other in a single pass?

### 4. Your Agents Are Re-Interpreting Upstream Decisions

The first agent decided the audience. The second agent read that decision and subtly re-interpreted it. "Mid-market tech" became "growth-stage startups" in the second agent's framing. The third agent read the second's output and shifted it further. "Growth-stage startups" became "early-stage founders." By the time the generation agent received its brief, the audience had been reinterpreted at every stage.

Nobody diverged dramatically at any single step. Each reinterpretation was small, reasonable, defensible. But they accumulated. The output addresses a slightly different audience at every level of its construction — the evidence was selected for mid-market tech, the format was chosen for growth-stage startups, the voice was calibrated for early-stage founders. It reads fine on the surface and feels off underneath.

This is composition drift. The fix is inheritance: downstream agents receive upstream decisions as structured, immutable inputs. They don't re-query the audience framework. They don't reinterpret the audience label. They receive "mid-market tech, confidence 87%, scored against ICP v3" and treat it as a given — the same way an architect treats the foundation dimensions as a given when designing the walls.

**The question:** Do your downstream agents inherit upstream decisions as-is, or does each one apply its own interpretation? Is there a context assembly layer that translates structured decisions into the form each downstream agent needs without allowing reinterpretation?

### 5. Your Agent Is Treating Empty Fields as Findings

A null field in the CRM becomes a "gap." A quiet period becomes "stalling." A missing relationship becomes "single-thread risk." Your agent is treating the absence of data as a signal — and sometimes it's right. A quiet period in a previously active enterprise account might genuinely indicate risk. But most of the time, nobody filled in the field. Or it wasn't relevant. Or the process didn't capture it. Or the rep tracks next steps in their own notes, not in the CRM.

Without explicit rules about when absence-as-signal reasoning is permitted, your agent defaults to treating every empty field as a finding. Because analytical writing trained it to treat noting gaps as thorough. The agent is trying to be comprehensive, and noting what's missing is part of being comprehensive. The problem is that what's "missing" from the data is often just what wasn't entered, and there's a massive difference between "this data doesn't exist" and "this data wasn't captured."

The fix is specific: define, per field or per field category, when absence is meaningful and when it's just missing data. Absence-as-signal reasoning should only be permitted in explicitly diagnostic contexts, for fields where absence has been defined as potentially meaningful, and with explicit acknowledgment of the alternative explanation (nobody filled it in).

**The question:** Has your system defined when absence is meaningful versus when it's just missing data? Does the agent know the difference between "this data doesn't exist" and "this data wasn't captured"?

### 6. Your System Is Acting on Single Observations

A human made one atypical edit. Your learning system captured it. Next run, the system adjusted its behaviour based on that single correction. One edit rippled through the entire pipeline.

A single observation is not a pattern. Two observations are not a pattern. The system needs several confirmed instances — across different contexts, over meaningful time — before even a soft runtime adjustment. And it needs sustained consistency over weeks before proposing a permanent framework change. If your learning system can act on a single correction, your system's behaviour is volatile — responsive to individual instances rather than sustained patterns.

The structural fix is separating observation from action. The observing agent writes to an observation store. A separate pattern-detection process reads that store on its own cycle. Only the pattern-detection process can propose changes. This prevents a single outlier from rippling through the system. It forces evidence accumulation. And it creates an audit trail — you can trace any behavioural change back to the pattern that caused it, through the observations that formed the pattern.

**The question:** Does your learning system require multiple confirmed instances before changing behaviour? Is the boundary between observation and action structural — enforced by system architecture — or aspirational — enforced by instructions the model might not follow?

### 7. Your Agent Has Frameworks It Doesn't Need

You loaded audience profiles into the validation agent "just in case." Now it's evaluating audience fit — even though the scoring agent already made that decision. You gave the content agent access to competitive analysis "for context." Now every piece includes competitive positioning whether it's relevant or not.

A model with a risk assessment framework loaded will find risks. A model with a scoring rubric will produce scores. A model with competitive data will make competitive comparisons. The analytical lens creates the finding, not the other way around. If you give an agent a tool, it will use the tool. The question isn't whether the agent can resist the temptation — it's why you put the temptation there.

Each agent should load only the minimum frameworks for its specific judgment. If an agent doesn't need to assess audience fit, don't load audience profiles. If an agent doesn't need to evaluate risks, don't load the risk framework. The agent can't misuse a framework it doesn't have.

**The question:** Does each agent load only what it needs for its specific judgment? Or are there frameworks loaded "just in case" that are creating analytical behaviours you didn't ask for?

### 8. Your Data Is Aging Without Anyone Noticing

A competitive signal from eight months ago sits in your knowledge store looking exactly like yesterday's intelligence. When an agent pulls it into context, it reasons against it with the same confidence it applies to current data. There's no mechanism in the model to distinguish fresh from stale — the data looks exactly the same in the context window regardless of when it was captured.

Your system didn't break. It's just increasingly wrong — reasoning against an outdated model of reality, producing high-confidence output that doesn't match what's actually happening. The symptoms are subtle: recommendations feel slightly off, analysis is technically defensible but doesn't match reality, the system just doesn't feel right anymore.

Decay architecture fixes this. Each data type gets an appropriate decay profile — event-driven, velocity-based, reinforcement-based, or threshold-based. A lifecycle process evaluates freshness before agents pull data into context. Agents receive freshness metadata alongside the intelligence and weight their reasoning accordingly.

**The question:** Does your intelligence layer have decay architecture? Does each data type have an appropriate decay profile? Or is everything in the active store treated as equally current regardless of when it was captured?

### 9. Your Humans Are in the Wrong Place

You put humans at every checkpoint, creating bottlenecks that slow the pipeline without producing useful learning signals. Every interruption fragments the agent's work — the human reacts to a partial output, produces a correction that applies to the partial state, and the agent resumes with a constraint that might not make sense for the complete output. Or you removed humans entirely, and the system runs on raw model capability with no external calibration.

The right placement: after the agent has done its complete work, before anything consequential happens. One meaningful decision point where the human reacts to a complete output. Their edit, their redirect, their approval — that's the learning signal. It's complete because they saw the complete output. It's meaningful because they were in a position to evaluate the whole, not just a fragment.

Too many checkpoints produce noise. Too few produce drift. The balance is one human decision point per judgment cycle, placed at the point where the human's domain expertise adds the most value and where their correction produces the cleanest learning signal.

**The question:** Where do humans sit in your loop? Are they reacting to complete outputs, or interrupting partial ones? Is their input producing clean learning signals, or fragmentary corrections?

### 10. Your Trust Boundaries Are Symmetric

Your system can upgrade its own autonomy as easily as it can downgrade it. The trust model — if it exists — treats escalation and de-escalation as equivalent operations. Or worse: the system defaults to high autonomy when the trust system is unavailable.

Every boundary should be asymmetric: fast toward safety, slow toward authority. Upgrades require sustained performance over meaningful time, multiple consistent results, and explicit human approval. Downgrades happen immediately on any trust incident — a single problematic output, a confidence miscalibration, a boundary violation.

If the trust system fails, default to maximum oversight — never default upward. A system that requires human approval when trust is uncertain might be slower. A system that assumes full autonomy when trust is uncertain will eventually cause damage nobody authorised.

**The question:** Can your system increase its own authority without human approval? What happens when the trust or quality system is unavailable — does it default to safety or to autonomy?

---

## What to Do With This

Each blind spot is a door. If one made you uncomfortable, that's the one worth investigating.

- For cross-pollination and vacuum problems → **Agent System Design** (judgment mapping, lens identification, scope definition)
- For knowledge and interpretation problems → **Agent Knowledge Curator** (reasoning frameworks, data reading guides, interpretation rules)
- For decay, drift, and cascade problems → **Agent Drift Prevention** (dependency mapping, decay profiling, drift surface)
- For an existing system that needs diagnosis → **Agent System Review**

---

## References

This skill loads all reference documents from all packages — it draws from the full design philosophy because every blind spot touches a different part of the design space.
