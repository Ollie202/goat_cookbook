---
name: goated-benchmark
description: Benchmark an existing product against reusable patterns observed in strong and winning builds, then identify the highest-leverage improvements without blindly rewriting, bloating, or destabilizing what already works.
---

# Goated Benchmark

A reusable benchmark for making products harder to dismiss, easier to understand, more trustworthy, more complete, and more competitive.

This is **not** a template that every product must copy. It is a pressure-test.

The goal is not to turn every project into the same architecture, add unnecessary infrastructure, or destroy a good product chasing a score. The goal is to expose weak claims, shallow integrations, missing proof, weak demos, fragile assumptions, and avoidable gaps before users, judges, investors, reviewers, or production traffic expose them for us.

Use this alongside `goated_foundation.md`:

- `goated_foundation.md` governs **how the project is organized and executed**.
- `goated_benchmark.md` governs **how strongly the product itself stands up to scrutiny**.

The core principle is:

> **Do not ask people to trust an important product claim when the product can prove it instead.**

---

# 1. Benchmarking philosophy

When comparing a build against this file:

1. **Preserve what already works.** Do not recommend a rewrite simply because another architecture is fashionable.
2. **Benchmark claims, not aesthetics alone.** Focus on the reasons a user or judge should believe the product is valuable and works as claimed.
3. **Prioritize the crux.** Fix the small number of weaknesses that most affect product value, trust, differentiation, judging criteria, or demo quality.
4. **Do not add complexity for scorekeeping.** A smaller system that proves its core thesis is stronger than a large system full of decorative features.
5. **Distinguish missing from unnecessary.** A benchmark gap matters only if it strengthens the actual product, rubric, user outcome, or proof.
6. **Use evidence over confidence.** Prefer reproducible measurements, external state, hashes, receipts, traces, test results, benchmark commands, or real integrations over assertions.
7. **Treat failures as product research.** Repeated or meaningful failures should become invariants, guards, tests, or explicit product behavior when appropriate.
8. **Respect project constraints.** Time, cost, solo-builder capacity, sponsor requirements, security, available infrastructure, and deadlines all matter.

The benchmark should make the product better, not merely larger.

---

# 2. The benchmark loop

Use this loop for an existing build:

```text
UNDERSTAND THE PRODUCT
        ↓
IDENTIFY THE CORE CLAIM / CRUX
        ↓
READ THE REAL RUBRIC / USER NEED / MARKET REQUIREMENT
        ↓
COMPARE CURRENT EVIDENCE AGAINST THE CLAIM
        ↓
FIND THE HIGHEST-LEVERAGE GAPS
        ↓
IMPROVE WITHOUT DESTROYING WORKING SYSTEMS
        ↓
TEST THE HAPPY PATH + ADVERSARIAL PATH
        ↓
MEASURE THE RESULT
        ↓
RECORD EVIDENCE
        ↓
REHEARSE THE STORY / DEMO
        ↓
RE-BENCHMARK
```

---

# 3. First identify the product crux

Every strong product should have a concise answer to:

> **What important problem does this solve better than the obvious alternative?**

Weak crux:

> AI platform for media workflows.

Stronger crux:

> A four-word edit should not force an expensive media pipeline to regenerate every downstream asset.

Weak crux:

> AI ad generator.

Stronger crux:

> Generative models may create the scene, but they must not silently alter the approved product, brand assets, claims, or export provenance.

Weak crux:

> AI operations agent.

Stronger crux:

> A hallucinated diagnosis must not turn directly into a destructive production action.

The crux should be:

- easy to explain;
- meaningful to a real user;
- specific enough to demonstrate;
- important enough that solving it matters;
- difficult to dismiss as another generic wrapper.

If the product has no identifiable crux, benchmark this before adding more features.

---

# 4. Rubric-first and requirement-first design

For competitions, hackathons, grants, platform challenges, enterprise pilots, or sponsor builds, treat the real evaluation criteria as a product requirement document.

Before optimizing the build, determine:

- what is explicitly scored;
- what is required versus optional;
- what the sponsor or platform actually wants demonstrated;
- which capabilities receive the most weight;
- what must be real rather than mocked;
- which constraints can disqualify a submission;
- what evidence a reviewer can independently verify.

Do not merely satisfy a requirement syntactically.

Bad sponsor integration:

```text
Generate artifact → upload artifact to sponsor storage → add sponsor logo
```

Stronger integration:

```text
Sponsor capability becomes necessary to the product's correctness,
performance, trust, economics, execution, or user value.
```

Ask:

> **If we removed the sponsor/platform technology, would the product become meaningfully worse or lose an important capability?**

If the answer is no, the integration may be decorative.

---

# 5. Sponsor-native / platform-native architecture

When a product is built for a specific ecosystem, use the platform where it is naturally load-bearing.

Examples of strong integration patterns:

- storage used for content-addressed verification, not just file hosting;
- blockchain used for settlement, enforcement, ownership, or verifiable state, not just writing a random hash on-chain;
- an agent framework used for meaningful orchestration, routing, tools, memory, or safety boundaries, not merely one API call;
- local GPU hardware used for a measurable latency, privacy, cost, or offline advantage;
- an observability platform used to detect and prove actual runtime behavior, not only display a dashboard;
- a database or vector store used because the product needs durable/queryable state, not because every AI app is expected to have one.

The correct question is not:

> How many sponsor features did we use?

It is:

> Which sponsor capabilities make our product more true, useful, differentiated, or defensible?

---

# 6. Build for proof, not only the happy path

A demo that only shows success proves very little.

For the core product claim, ask:

- What would silently make this claim false?
- What failure would fool a user while the UI still looks healthy?
- What malformed, stale, tampered, delayed, missing, duplicated, or adversarial input matters?
- What happens when a provider times out?
- What happens when an external service lies, changes, disappears, or returns partial state?
- What happens when the model is confidently wrong?
- What happens when stored state disagrees with source-of-truth state?

Then build at least one meaningful negative or adversarial demonstration when appropriate.

A strong demo pattern is:

```text
1. Show the normal system.
2. Introduce a realistic failure or tampering event.
3. Let the output appear deceptively normal if that reflects the real risk.
4. Show the system detect the discrepancy.
5. Show the safe response, fallback, quarantine, refusal, or recovery.
6. Show the evidence explaining what happened.
```

A product that catches an important failure live is often more memorable than one that only generates a successful result.

---

# 7. Bound what AI is allowed to decide

When models are involved, decide explicitly where probabilistic behavior is acceptable and where deterministic guarantees are required.

A useful pattern is:

```text
AI MAY PROPOSE / GENERATE / CLASSIFY / REASON
                     ↓
DETERMINISTIC CHECKS / POLICY / SOURCE-OF-TRUTH VALIDATION
                     ↓
SAFE ACTION / EXPORT / EXECUTION
```

Ask:

- Which outputs may safely be creative?
- Which values must be copied exactly?
- Which actions are irreversible?
- Which decisions require external grounding?
- Which claims require deterministic validation?
- Which state must be independently re-read rather than trusted from cached application state?

Do not add cryptography, consensus, blockchains, or elaborate policy engines merely because they sound rigorous. Use the simplest boundary that actually protects the product's important invariant.

---

# 8. Failure → invariant → automated protection

When development reveals an important failure, do more than patch the one instance.

Use this conversion:

```text
FAILURE DISCOVERED
      ↓
WHY COULD THIS HAPPEN?
      ↓
GENERAL FAILURE CLASS
      ↓
PRODUCT / SYSTEM INVARIANT
      ↓
GUARD, TEST, AUDIT, VALIDATION, OR STATE MACHINE
      ↓
REGRESSION PROTECTION
```

Example:

```text
A language renders as empty glyphs
        ↓
The selected font does not contain every rendered character
        ↓
Invariant: every rendered character must exist in the selected font
        ↓
Automated glyph-coverage audit
```

Another example:

```text
Tests pass but incremental rebuild behavior is wrong
        ↓
Two subsystems use incompatible source fingerprints
        ↓
Invariant: one canonical fingerprint definition governs reuse decisions
        ↓
Cross-system contract test + real scenario benchmark
```

This is how bugs become long-term product quality rather than repeated regressions.

---

# 9. Replace important trust assumptions with receipts

For each important claim, ask:

> **What is the receipt?**

Possible receipts include:

- SHA-256 or content hashes;
- signed events;
- transaction hashes;
- immutable or append-only records;
- source revision / commit SHA;
- model ID and revision;
- deterministic seed;
- execution trace;
- storage root;
- deployment address;
- benchmark output;
- audit result;
- test run;
- provider response ID;
- timestamped event history;
- independently retrievable bytes;
- provenance manifest;
- reconciliation result;
- export manifest.

Not every app needs cryptographic receipts. The point is to provide the strongest practical evidence appropriate to the claim.

Weak:

> Status: Verified.

Stronger:

> Verified against source revision `X`, retrieved artifact `Y`, recomputed hash `Z`, and recorded the exact verification result.

The more important the claim, the less it should depend on a decorative green badge.

---

# 10. Independently verify important state

Do not let the same component both make a claim and be the only evidence that the claim is true when independent verification is practical.

Examples:

- do not trust a database row saying an object exists if the product depends on the actual bytes still being present and intact;
- do not trust a generated report saying deployment succeeded if the chain/provider can be queried directly;
- do not trust a model to certify its own output when deterministic checks are available;
- do not trust a UI badge if the underlying state can be re-derived;
- do not trust a cached artifact if the source-of-truth can be fingerprinted again.

A useful design question:

> **If this claim were wrong but every internal status field still said success, how would we catch it?**

If the answer is “we would not,” determine whether the claim is important enough to deserve an independent check.

---

# 11. Quantify the headline claim

Strong builds turn their core value proposition into a number a reviewer can remember.

Examples:

```text
18 total nodes
4 rebuilt
14 reused
10 provider calls avoided
```

```text
Cold run: 71.7s
Warm run: 45.4s
90/90 checks passed
0 outbound connections
```

```text
Reference workflow: ~9 hours
Our workflow: ~2 hours
```

Good metrics are:

- directly related to the crux;
- easy to reproduce;
- measured on the real system;
- specific about environment and inputs;
- difficult to inflate with vanity statistics.

Useful categories include:

- latency;
- cost;
- provider calls avoided;
- throughput;
- error rate;
- recovery time;
- verification success;
- deterministic reuse;
- storage reduction;
- build time;
- user steps eliminated;
- task completion time;
- accuracy on a defined test set;
- hardware utilization;
- offline/private execution;
- number of critical checks passed.

Avoid metrics that sound impressive but do not strengthen the product claim.

---

# 12. Make benchmarks reproducible

A benchmark is stronger when another person or fresh agent can regenerate it.

Prefer:

```text
checked-in command / script
+ fixed or documented fixture
+ environment description
+ raw result
+ summarized result
```

Avoid manually typing performance numbers into a README without preserving how they were obtained.

For meaningful benchmark claims, record:

- exact command;
- relevant hardware/software versions;
- input fixture;
- warm/cold state when relevant;
- number of runs;
- raw output or evidence location;
- caveats.

Do not fabricate precision.

---

# 13. Production-readiness should support the thesis

Production-readiness is not “add Kubernetes.”

Evaluate only the operational qualities that matter to the actual product:

- failure handling;
- retries and idempotency;
- observability;
- reconciliation;
- permissions / least privilege;
- secret handling;
- durable state;
- data lifecycle;
- integrity checks;
- queue/background execution;
- rate limits;
- concurrency;
- recovery behavior;
- deployment reproducibility;
- user-facing error states;
- safety around irreversible actions.

If the competition explicitly scores production readiness, make these qualities visible in the demo and evidence rather than assuming judges will infer them from the source code.

---

# 14. Complete the vertical slice before widening the surface area

A narrower complete system is usually stronger than a giant partially working one.

Prefer:

```text
real user input
→ real core logic
→ real sponsor/provider integration
→ real persisted/executed result
→ real failure handling
→ real evidence
→ polished demonstration
```

before adding:

- five additional dashboards;
- a huge settings surface;
- ten speculative integrations;
- unsupported future modes;
- decorative analytics;
- unnecessary microservices;
- fake marketplace/community features;
- enterprise features with no real implementation.

The best additional feature is often the one that makes the existing core claim more undeniable.

---

# 15. Demo design is part of product engineering

A strong product can lose because the demo hides the reason it is strong.

The demo should answer quickly:

1. What problem exists?
2. Why does the obvious solution fail?
3. What does our product do differently?
4. Where is the sponsor/platform capability actually used?
5. What is the “holy shit” moment?
6. What measurable result proves the claim?
7. What happens when something goes wrong?
8. What evidence remains afterward?

A reliable demo arc is:

```text
PROBLEM
  ↓
NAIVE / EXISTING FAILURE
  ↓
OUR CORE MECHANIC
  ↓
LIVE SUCCESS
  ↓
ADVERSARIAL OR FAILURE CASE
  ↓
DETECTION / RECOVERY / REFUSAL
  ↓
MEASURABLE RESULT
  ↓
RECEIPT / EVIDENCE
```

Do not spend most of a short demo clicking through navigation.

---

# 16. Make the product easy for a judge or reviewer to score

Do not make a reviewer infer that requirements were satisfied.

For competitions, maintain a simple requirements matrix:

| Criterion | Weight | Where implemented | Demo moment | Evidence |
|---|---:|---|---|---|
| Example criterion | 30% | `packages/...` | 01:20 | test/URL/hash |

Before submission, every important scored criterion should have:

- implementation;
- visible proof;
- a demo moment;
- evidence;
- honest caveats where incomplete.

A judge should be able to award points without reverse-engineering the repository.

---

# 17. Differentiate through engineering, not only features

Many hackathons contain dozens of projects with similar surface features.

Differentiation can come from:

- a better problem framing;
- a non-obvious invariant;
- stronger verification;
- better failure handling;
- lower cost;
- lower latency;
- local/offline execution;
- deterministic behavior where others are probabilistic;
- tighter sponsor integration;
- clearer user workflow;
- better evidence/provenance;
- stronger interoperability;
- safer execution;
- better recovery;
- more complete end-to-end execution.

Ask:

> **If ten other teams use the same models and sponsor SDK, why would our architecture still be memorable?**

---

# 18. Benchmark the obvious alternative

Whenever possible, compare against the actual baseline a user would otherwise use.

Examples:

- full regeneration vs dependency-aware regeneration;
- naive agent action vs grounded/verified action;
- cloud execution vs local execution;
- manual workflow vs automated workflow;
- unverified artifact vs independently verified artifact;
- first run vs cached/incremental run;
- sponsor reference implementation vs optimized implementation.

A baseline turns an abstract improvement into a concrete advantage.

Do not cherry-pick a deliberately broken baseline. Use the strongest fair comparison available within the time and evidence constraints.

---

# 19. Winning-pattern references

The following examples are **benchmark references, not architectures to copy blindly**. Extract the reusable lesson.

## TakeGraph-style lesson: incremental work + independent correctness

Observed winning pattern:

- model a generation pipeline as dependencies rather than one monolithic run;
- rebuild only invalidated downstream work;
- fingerprint inputs and outputs;
- verify reusable assets against the actual stored bytes;
- expose machine-readable reasons for reuse/rebuild decisions;
- demonstrate provider failure and structured recovery;
- measure avoided work;
- convert a discovered hashing inconsistency into a canonical invariant and stronger verification.

Reusable lesson:

> **Optimization claims become much stronger when reuse is deterministic, externally checked, measurable, and explainable.**

Do not copy a dependency graph into products that do not need one.

## Rivet-style lesson: bounded creativity + deterministic brand integrity

Observed winning pattern:

- let generative models create the parts where creativity is valuable;
- prevent them from redrawing exact assets that must remain faithful;
- deterministically composite approved product/logo/typography assets;
- audit output before export;
- record lineage, model revision, seeds, timings, and checks;
- tamper with approved input in the demo and refuse export when hashes disagree;
- benchmark cold/warm local GPU execution;
- convert real development failures into permanent audits.

Reusable lesson:

> **Use AI where variability helps; use deterministic controls where correctness matters. Then prove the boundary works.**

Do not add hashes or deterministic compositing where the product has no important fidelity requirement.

## Backstop-style lesson: model output is not permission to act

Observed winning pattern:

- AI proposes diagnosis/action;
- real infrastructure signals ground the diagnosis;
- guardrails verify whether execution is allowed;
- unsafe or hallucinated actions are blocked/rerouted;
- the demo intentionally introduces a bad model conclusion;
- the system shows why naive direct execution would be dangerous.

Reusable lesson:

> **In agentic systems, reasoning and authority should be separate when actions can cause real damage.**

## On-chain enforcement-style lesson

Observed winning pattern:

- AI or software helps structure a decision;
- funds/state/rights are enforced by an external deterministic system;
- the resulting action leaves an independently inspectable record.

Reusable lesson:

> **Use decentralized infrastructure when independent enforcement or verifiable shared state is part of the product, not as decorative provenance.**

## Cross-source integrity-style lesson

Observed winning pattern:

- do not trust one source of operational truth;
- compare agent logs, source control, CI, external services, or runtime state;
- derive a result from multiple independent signals.

Reusable lesson:

> **When any one evidence source can lie or drift, cross-verification can turn weak telemetry into a stronger integrity claim.**

---

# 20. The Goated Benchmark scorecard

Score only dimensions that materially apply to the product. Mark irrelevant dimensions `N/A`; do not invent work solely to gain points.

A useful default score is 100 points.

## A. Problem + crux — 10

- 0–3: generic problem, unclear user pain.
- 4–6: real problem but weak differentiation.
- 7–8: sharp, demonstrable product thesis.
- 9–10: memorable crux tied directly to meaningful user value.

## B. Requirement / rubric fit — 10

- 0–3: major requirements unknown or weakly addressed.
- 4–6: requirements mostly satisfied but hard to verify.
- 7–8: strong direct mapping from requirements to implementation.
- 9–10: product and demo make the highest-value criteria undeniable.

For non-competition products, substitute actual customer, market, regulatory, or operational requirements.

## C. Core vertical-slice completeness — 10

- 0–3: prototype/scaffolding only.
- 4–6: core path works with gaps or mocks.
- 7–8: real end-to-end core path works.
- 9–10: end-to-end path plus meaningful failure behavior and recovery are proven.

## D. Integration depth — 10

- 0–3: decorative or superficial integration.
- 4–6: useful but replaceable integration.
- 7–8: platform meaningfully improves the product.
- 9–10: platform capability is load-bearing to product value/correctness/performance/trust.

## E. Evidence + verifiability — 10

- 0–3: claims mostly asserted.
- 4–6: tests/logs exist but key claims remain self-reported.
- 7–8: important claims have real evidence.
- 9–10: critical claims can be independently reproduced or verified.

## F. Failure / adversarial resilience — 10

- 0–3: happy path only.
- 4–6: basic errors handled.
- 7–8: meaningful failure classes tested.
- 9–10: adversarial demo proves the core safety/correctness mechanism under realistic failure.

## G. Measurable advantage — 10

- 0–3: value is qualitative only.
- 4–6: some metrics but weak baseline/reproducibility.
- 7–8: strong headline metric tied to product crux.
- 9–10: fair baseline + reproducible benchmark + memorable improvement.

## H. Engineering / production credibility — 10

- 0–3: fragile demo code.
- 4–6: reasonable implementation with obvious operational gaps.
- 7–8: appropriate tests, state handling, observability, permissions, recovery, or deployment discipline.
- 9–10: production qualities directly support the thesis and are visibly proven.

## I. Demo clarity + memorability — 10

- 0–3: difficult to understand or navigation-heavy.
- 4–6: understandable but generic.
- 7–8: clear problem → mechanism → result story.
- 9–10: strong live proof/adversarial moment + memorable metric + clear evidence.

## J. Scope discipline + differentiation — 10

- 0–3: bloated, scattered, or indistinguishable.
- 4–6: useful but too broad or generic.
- 7–8: focused build with recognizable technical/product identity.
- 9–10: every major feature strengthens the core thesis and the product remains distinct even among similar SDK/model choices.

### Score interpretation

```text
90–100  Exceptional benchmark strength. Focus on polish, evidence gaps, and submission execution.
80–89   Strong. Fix the few gaps that most affect the crux or rubric.
70–79   Competitive but vulnerable. Several high-leverage weaknesses remain.
60–69   Functional build, weak competitive proof. Prioritize aggressively.
<60     Do not add random features. Revisit the crux, vertical slice, proof, and requirement fit.
```

Do not worship the total. A 92 with a fatal missing requirement can still lose. A 78 with an extraordinary crux and demo can outperform a mechanically scored 90.

---

# 21. Evidence grades

When benchmarking a claim, classify the evidence level.

```text
E0 — Idea only
E1 — Code/scaffolding exists
E2 — Unit/mock proof
E3 — Real local end-to-end proof
E4 — Real external/provider/hardware/network proof
E5 — Independently reproducible/verifiable proof
```

For the product's central claims, aim for the highest practical evidence grade before submission or release.

Do not describe an E2 integration as if it were E4.

---

# 22. Gap prioritization

After scoring, do **not** start implementing every low-scoring item.

Rank gaps by:

```text
Priority = Impact × Relevance × Evidence Gain × Demo Value
           -----------------------------------------------
                    Cost × Risk × Scope Creep
```

You do not need literal arithmetic. Use the model to force prioritization.

Prefer work that:

- fixes a high-weight rubric gap;
- proves the core thesis;
- turns a claim into evidence;
- creates a memorable demo moment;
- addresses a realistic failure;
- deepens a sponsor-native integration;
- produces a measurable result;
- completes the vertical slice.

Deprioritize work that:

- only increases feature count;
- creates infrastructure with no user/judge value;
- rewrites stable components without a proven reason;
- adds speculative scale before the core flow works;
- makes the demo longer without making the thesis clearer;
- introduces a new dependency merely to look sophisticated.

---

# 23. Benchmark report format for agents

When asked:

```text
Compare our current build against goated_benchmark.md.
```

The agent should first inspect the actual repository, current state, relevant issues/PRs, tests, docs, deployment evidence, competition requirements, and live integration status when accessible.

Then return:

```markdown
# Goated Benchmark Review

## Product crux
One sentence describing the current thesis.

## Current score
XX/100

## Strongest areas
- What is already genuinely strong.
- Evidence supporting each strength.

## Highest-leverage gaps
1. Gap
   - Why it matters
   - Current evidence level
   - Desired evidence level
   - Smallest strong improvement
   - Risk / cost

2. ...

## Do NOT change
- Existing strengths or architectural decisions that should be preserved.

## Recommended next moves
1. Highest-value action
2. Next action
3. Next action

## Demo / proof opportunity
The strongest adversarial, measurable, or independently verifiable demonstration currently available.

## Rubric / user impact
Exactly which requirement or user outcome each recommendation improves.
```

The benchmark review should be specific to the current repository. Generic advice is a failure.

---

# 24. Rules for modifying a build after benchmarking

If the user asks the agent to **improve the build using this benchmark**, the agent should:

1. read `goated_foundation.md` if present;
2. read the target project's `AGENTS.md`, `PROJECT_STATE.md`, current sprint, requirements/rubric, and relevant architecture docs;
3. inspect current code, tests, issues, PRs, and real integration evidence;
4. identify the highest-leverage benchmark gaps;
5. preserve settled architecture unless evidence justifies changing it;
6. convert improvements into bounded issues/acceptance criteria when the project foundation uses that workflow;
7. implement incrementally on focused branches;
8. test success and meaningful failure paths;
9. record benchmark/evidence results;
10. re-score honestly after the improvement.

Do not perform a wholesale rewrite unless the current architecture fundamentally prevents the core product claim and the evidence supports that conclusion.

---

# 25. Anti-patterns

Avoid:

- sponsor-logo integrations;
- “AI-powered” as the main differentiation;
- dashboards hiding an incomplete core workflow;
- fake production-readiness;
- mocked integrations presented as real;
- self-certifying verification systems with no independent check;
- random blockchain hashes with no enforcement or user value;
- arbitrary multi-agent architectures;
- impressive test counts that do not test important claims;
- benchmark numbers with no reproducible procedure;
- adding security theater unrelated to the threat model;
- chasing every possible failure instead of the meaningful ones;
- shipping ten mediocre features instead of one undeniable core mechanic;
- changing working architecture merely because another winner used something different;
- copying another winning product's domain-specific mechanism without the underlying need.

---

# 26. Pre-submission / pre-release pressure test

Before a consequential demo, launch, release, or hackathon submission, answer:

- Can a stranger explain the product after one minute?
- Is the core problem real and specific?
- Is our differentiation structural or merely cosmetic?
- Does the central workflow work end to end without hidden mocks?
- Are sponsor/platform features genuinely load-bearing where relevant?
- What is the most important claim we currently ask people to trust?
- Can we prove that claim instead?
- What realistic failure would make us look foolish if it happened during judging?
- Have we tested it?
- What is our memorable quantitative result?
- Can that result be reproduced?
- What is our strongest receipt/evidence artifact?
- Does the demo expose the core technical insight quickly?
- Can the judge map the build directly to the scoring rubric?
- Are we overclaiming anything?
- What should we deliberately **not** add before the deadline?

---

# 27. Living benchmark protocol

This file is expected to evolve as more strong products, failures, competition results, postmortems, and winning patterns are studied.

When adding a new benchmark reference:

1. verify what the product actually built;
2. verify why it likely scored well using organizer/judge/rubric evidence where possible;
3. distinguish fact from inference;
4. extract the reusable principle;
5. avoid copying domain-specific implementation details unless they generalize;
6. add or refine a benchmark criterion only if it improves future product decisions;
7. remove stale rules that create bloat without predictive value.

A new winner should not automatically create a new rule.

The benchmark should improve through **signal accumulation**, not checklist accumulation.

---

# 28. The final Goated test

A strong build should increasingly be able to answer yes to these questions:

```text
Do we solve a sharp real problem?
Do we have a memorable reason to exist?
Does the architecture directly support that reason?
Does the required platform/sponsor technology matter to the product?
Does the core flow work for real?
Can we survive at least the important failure paths?
Can we prove the claims that matter?
Can we quantify the advantage?
Can another person reproduce or inspect the evidence?
Can we demonstrate all of this quickly?
Did we avoid unnecessary complexity while doing it?
```

If yes, the product is not merely more feature-complete.

It is becoming **harder to dismiss**.

---

# Invocation examples

```text
Compare our current build against goated_benchmark.md. Do not rewrite the product. Identify the highest-leverage gaps, preserve what is already strong, and tell me the smallest changes that would materially improve our score, proof, demo, and chances of winning.
```

```text
Use goated_benchmark.md and the actual hackathon rubric to pressure-test this repo. Verify current implementation before scoring it. Separate proven capabilities from mocks/plans, rank the top five gaps by impact, and do not recommend feature bloat.
```

```text
Benchmark this project against goated_benchmark.md, then turn only the top three justified improvements into bounded issues with acceptance criteria. Do not change settled architecture unless you can show why it blocks the product crux.
```

```text
Re-score this build against goated_benchmark.md after the latest milestone. Show what evidence improved, what still depends on trust, and what one demo moment would make the product most difficult for a judge to dismiss.
```
