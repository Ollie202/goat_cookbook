---
name: goated-benchmark
description: Pressure-test an existing product against reusable patterns from strong and winning builds, then identify the highest-leverage improvements without blindly rewriting, bloating, or destabilizing what already works.
---

# Goated Benchmark

A reusable benchmark for making products harder to dismiss, easier to understand, more trustworthy, more complete, and more competitive.

This is **not** a template every product must copy. It is a pressure-test.

Use it alongside `goated_foundation.md`:

- `goated_foundation.md` governs **how the project is organized and executed**.
- `goated_benchmark.md` governs **how strongly the product itself stands up to scrutiny**.

Core principle:

> **Do not ask people to trust an important product claim when the product can prove it instead.**

The benchmark should make the product better, not merely larger.

---

# 1. How to use this benchmark

When comparing a build against this file:

1. **Preserve what already works.** Do not recommend rewrites because another architecture is fashionable.
2. **Benchmark claims, not aesthetics alone.** Focus on why a user or judge should believe the product is valuable and works as claimed.
3. **Prioritize the crux.** Fix the few weaknesses that most affect product value, trust, differentiation, rubric fit, or demo quality.
4. **Do not add complexity for scorekeeping.** A narrow system that proves its thesis is stronger than a broad system full of decorative features.
5. **Distinguish missing from unnecessary.** A benchmark gap matters only when fixing it strengthens the real product, requirement, user outcome, or proof.
6. **Use evidence over confidence.** Prefer measurements, external state, hashes, receipts, traces, test results, benchmark commands, or real integrations over assertions.
7. **Treat meaningful failures as product research.** Convert recurring failure classes into invariants, guards, tests, audits, or explicit product behavior.
8. **Respect constraints.** Time, cost, solo-builder capacity, security, sponsor requirements, infrastructure, and deadlines matter.

Default loop:

```text
UNDERSTAND PRODUCT + RUBRIC / USER NEED
                ↓
IDENTIFY THE CORE CLAIM / CRUX
                ↓
INSPECT WHAT REALLY WORKS TODAY
                ↓
COMPARE CLAIMS AGAINST EVIDENCE
                ↓
FIND HIGHEST-LEVERAGE GAPS
                ↓
IMPROVE WITHOUT DESTROYING STRENGTHS
                ↓
TEST HAPPY + MEANINGFUL FAILURE PATHS
                ↓
MEASURE + RECORD EVIDENCE
                ↓
REHEARSE DEMO / USER STORY
                ↓
RE-BENCHMARK
```

---

# 2. Find the product crux first

Every strong product should answer:

> **What important problem does this solve better than the obvious alternative?**

The crux should be:

- easy to explain;
- meaningful to a real user;
- specific enough to demonstrate;
- important enough that solving it matters;
- difficult to dismiss as another generic wrapper.

Examples:

Weak:

> AI media platform.

Stronger:

> A four-word edit should not force an expensive media pipeline to regenerate every downstream asset.

Weak:

> AI ad generator.

Stronger:

> Generative models may create the scene, but they must not silently alter approved products, brand assets, claims, or export provenance.

Weak:

> AI operations agent.

Stronger:

> A hallucinated diagnosis must not turn directly into a destructive production action.

If the product has no clear crux, benchmark that before adding features.

---

# 3. Treat the real rubric or requirement as a product requirement

For hackathons, competitions, grants, platform challenges, enterprise pilots, or sponsor builds, determine:

- what is explicitly scored;
- what is required versus optional;
- which capabilities receive the most weight;
- what must be real rather than mocked;
- what can disqualify the submission;
- what the sponsor/platform actually wants demonstrated;
- what evidence a reviewer can independently inspect.

Do not merely satisfy requirements syntactically.

Bad sponsor integration:

```text
Generate artifact → upload to sponsor service → add sponsor logo
```

Stronger integration:

```text
Sponsor capability is necessary to the product's
correctness, performance, trust, economics, execution, or user value.
```

Ask:

> **If we removed the sponsor/platform technology, would the product become meaningfully worse or lose an important capability?**

If not, the integration may be decorative.

Examples of naturally load-bearing integrations:

- storage used for integrity/retrieval guarantees rather than merely file hosting;
- blockchain used for settlement, enforcement, ownership, or verifiable shared state rather than a random hash;
- an agent framework used for meaningful orchestration, routing, tools, memory, or safety boundaries rather than one API call;
- local hardware used for measurable latency, privacy, offline, or cost advantages;
- observability used to detect and prove runtime behavior rather than merely display a dashboard.

Use only what strengthens the actual product.

---

# 4. Separate generation/reasoning from authority

When AI, agents, automation, or other probabilistic systems are involved, explicitly decide what they may **propose** and what they may **authorize**.

Core rule:

> **Generating or recommending something is not automatically permission to ship, publish, transfer, deploy, or execute it.**

A useful pattern is:

```text
AI / SYSTEM PROPOSES, GENERATES, CLASSIFIES, OR REASONS
                         ↓
DETERMINISTIC CHECK / POLICY / SOURCE-OF-TRUTH VALIDATION
                         ↓
AUTHORIZED ACTION / EXPORT / EXECUTION
```

Depending on the product, the authority boundary may be a deterministic check, policy engine, simulation, signature, external state read, human approval, or another mechanism appropriate to the risk.

Ask:

- Which outputs may safely be creative?
- Which values must remain exact?
- Which actions are irreversible or financially meaningful?
- Which claims require external grounding?
- Which decisions require deterministic validation?
- Which state should be independently re-read rather than trusted from cached application state?

Do not add cryptography, blockchains, consensus, policy engines, or human gates merely because they sound rigorous. Use the simplest boundary that protects the important invariant.

---

# 5. Complete the vertical slice before widening the surface area

Prefer a narrow real system:

```text
real user input
→ real core logic
→ real sponsor/provider integration where required
→ real persisted/executed result
→ real failure handling
→ real evidence
→ polished demonstration
```

before adding:

- more dashboards;
- a huge settings surface;
- speculative integrations;
- unsupported future modes;
- decorative analytics;
- unnecessary microservices;
- fake marketplace/community features;
- enterprise features with no real implementation.

The best additional feature is often the one that makes the existing core claim more undeniable.

---

# 6. Build for proof, not only the happy path

For the core claim, ask:

- What could silently make this claim false?
- What failure would fool a user while the UI still looks healthy?
- What malformed, stale, tampered, delayed, missing, duplicated, or adversarial input matters?
- What happens when a provider times out or returns partial state?
- What happens when the model is confidently wrong?
- What happens when stored state disagrees with source-of-truth state?

When appropriate, build at least one meaningful negative or adversarial demonstration.

Strong demo pattern:

```text
1. Show the normal system.
2. Introduce a realistic failure or tampering event.
3. Let the output appear deceptively normal if that reflects the risk.
4. Show the system detect the discrepancy.
5. Show the safe response, fallback, quarantine, refusal, or recovery.
6. Show the evidence explaining what happened.
```

A product that catches an important failure live can be more memorable than one that only produces a successful output.

---

# 7. Failure → invariant → automated protection

Do more than patch meaningful failures once.

```text
FAILURE DISCOVERED
      ↓
GENERAL FAILURE CLASS
      ↓
SYSTEM / PRODUCT INVARIANT
      ↓
GUARD, TEST, AUDIT, VALIDATION, OR STATE MACHINE
      ↓
REGRESSION PROTECTION
```

Example:

```text
Characters render as empty glyphs
→ selected font lacks required glyphs
→ invariant: every rendered character must exist in the selected font
→ automated glyph-coverage audit
```

Example:

```text
Tests pass but incremental rebuild behavior is wrong
→ two subsystems use incompatible fingerprints
→ invariant: one canonical fingerprint governs reuse
→ cross-system contract test + real scenario benchmark
```

Bugs should improve the long-term system when they reveal a reusable failure class.

---

# 8. Replace important trust assumptions with inspectable receipts

For every important claim, ask:

> **What is the receipt?**

When practical, successful execution should leave an inspectable artifact showing **what happened, why the system considered it valid, and what evidence supports that conclusion**.

A receipt may be:

- content hash;
- source revision / commit SHA;
- signed event or attestation;
- transaction hash;
- execution trace;
- storage root or retrieval proof;
- deployment address;
- model ID/revision and deterministic seed;
- audit result;
- benchmark output;
- test run;
- timestamped event history;
- provenance/export manifest;
- independently retrievable bytes;
- reconciliation result.

Not every app needs a cryptographic receipt. Use the strongest practical evidence appropriate to the claim.

Weak:

> Status: Verified.

Stronger:

> Verified against source revision `X`, retrieved artifact `Y`, recomputed hash `Z`, and recorded the exact result.

The more important the claim, the less it should depend on a decorative green badge.

---

# 9. Independently verify important state

When practical, do not let the same component both make a critical claim and be the only evidence that the claim is true.

Examples:

- do not trust a database row saying an object exists if the product depends on the actual bytes being present and intact;
- do not trust a deployment report if the real chain/provider can be queried directly;
- do not let a model certify its own output when deterministic checks are available;
- do not trust a UI badge if the underlying state can be re-derived;
- do not trust cached state when the source-of-truth can be checked cheaply enough.

Ask:

> **If this claim were wrong but every internal status field still said success, how would we catch it?**

If the answer is “we would not,” decide whether the claim is important enough to deserve an independent check.

---

# 10. Quantify the headline claim and benchmark it fairly

Strong builds turn their core value proposition into a memorable number.

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

Good metrics are:

- directly tied to the crux;
- measured on the real system;
- compared with a fair baseline where useful;
- specific about environment and inputs;
- reproducible when practical;
- difficult to inflate with vanity statistics.

Useful categories include latency, cost, throughput, recovery time, provider calls avoided, storage reduction, task completion time, accuracy on a defined test set, user steps removed, local/offline execution, and critical checks passed.

Benchmark against the obvious real alternative when possible:

- full regeneration vs dependency-aware regeneration;
- naive action vs grounded/verified action;
- cloud vs local execution;
- manual vs automated workflow;
- unverified vs independently verified artifact;
- first run vs cached/incremental run;
- sponsor reference implementation vs a justified improvement.

Do not cherry-pick a deliberately weak baseline.

For important benchmark claims, preserve:

```text
checked-in command / script
+ documented fixture
+ environment description
+ raw result
+ summarized result
+ caveats
```

Do not fabricate precision.

---

# 11. Production credibility should support the thesis

Production-readiness is not “add Kubernetes.”

Evaluate only operational qualities that matter to the product, such as:

- failure handling, retries, idempotency;
- observability and reconciliation;
- permissions / least privilege;
- secret handling;
- durable state and data lifecycle;
- integrity checks;
- rate limits / concurrency;
- recovery behavior;
- deployment reproducibility;
- user-facing error states;
- safety around irreversible actions.

If production readiness is explicitly scored, make relevant qualities visible in the demo/evidence rather than assuming judges will infer them from source code.

---

# 12. Design the demo as part of the product

A strong product can lose because the demo hides why it is strong.

The demo should answer quickly:

1. What problem exists?
2. Why does the obvious solution fail?
3. What does our product do differently?
4. Where does the sponsor/platform capability matter?
5. What is the memorable “holy shit” moment?
6. What measurable result proves the claim?
7. What happens when something goes wrong?
8. What evidence remains afterward?

Reliable arc:

```text
PROBLEM
  ↓
NAIVE / EXISTING FAILURE
  ↓
OUR CORE MECHANIC
  ↓
LIVE SUCCESS
  ↓
MEANINGFUL FAILURE / ADVERSARIAL CASE
  ↓
DETECTION / RECOVERY / REFUSAL
  ↓
MEASURABLE RESULT
  ↓
RECEIPT / EVIDENCE
```

Do not spend most of a short demo clicking through navigation.

For competitions, maintain a simple requirement map:

| Criterion | Weight | Where implemented | Demo moment | Evidence |
|---|---:|---|---|---|
| Example | 30% | `packages/...` | 01:20 | test/URL/hash |

A judge should not have to reverse-engineer the repository to award points.

---

# 13. Differentiate through engineering, not only feature count

If ten teams use the same models and sponsor SDK, why is this build still memorable?

Differentiation can come from:

- sharper problem framing;
- a non-obvious invariant;
- stronger verification;
- better failure handling or recovery;
- lower cost or latency;
- local/offline execution;
- deterministic behavior where others are probabilistic;
- deeper sponsor integration;
- clearer user workflow;
- stronger evidence/provenance;
- safer execution;
- more complete end-to-end execution.

Do not confuse more features with more differentiation.

---

# 14. Winning-pattern references

These are **reference patterns, not architectures to copy blindly**.

## TakeGraph-style lesson — incremental work + independent correctness

Observed pattern:

- model expensive work as dependencies;
- rebuild only invalidated work;
- fingerprint inputs/outputs;
- verify reusable assets against actual stored bytes;
- expose reasons for reuse/rebuild;
- demonstrate provider failure and structured recovery;
- measure avoided work;
- convert discovered fingerprint inconsistency into a canonical invariant.

Reusable lesson:

> **Optimization claims become stronger when reuse is deterministic, externally checked, measurable, and explainable.**

## Rivet-style lesson — bounded creativity + enforced export boundary

Observed pattern:

- let models create where variability is valuable;
- keep exact approved assets outside the model's creative authority;
- audit output before export;
- refuse export when required checks fail;
- leave a Campaign Receipt showing lineage/checks;
- tamper with approved input during the demo and detect it;
- benchmark real local hardware execution;
- convert real development failures into permanent audits.

Reusable lessons:

> **Use AI where variability helps; use deterministic controls where correctness matters.**

> **Generation is not permission to ship. Put an explicit authority boundary before consequential output.**

> **A successful result is stronger when it leaves an inspectable receipt explaining why it was accepted.**

## Backstop-style lesson — reasoning is not permission to act

Observed pattern:

- AI proposes diagnosis/action;
- real infrastructure signals ground the diagnosis;
- guardrails verify whether execution is allowed;
- unsafe or hallucinated actions are blocked/rerouted;
- the demo intentionally introduces a bad model conclusion.

Reusable lesson:

> **In agentic systems, reasoning and authority should be separate when actions can cause real damage.**

## On-chain enforcement-style lesson

Reusable lesson:

> **Use decentralized infrastructure when independent enforcement or verifiable shared state is part of the product, not as decorative provenance.**

## Cross-source integrity-style lesson

Reusable lesson:

> **When one evidence source can lie or drift, cross-verification can turn weak telemetry into a stronger integrity claim.**

---

# 15. Goated Benchmark scorecard — 100 points

Score only dimensions that materially apply. Mark irrelevant dimensions `N/A`; do not invent work solely to gain points.

## A. Problem + crux — 10

- 0–3: generic problem / unclear user pain.
- 4–6: real problem but weak differentiation.
- 7–8: sharp, demonstrable thesis.
- 9–10: memorable crux tied directly to meaningful value.

## B. Requirement / rubric fit — 10

- 0–3: major requirements unknown or weakly addressed.
- 4–6: mostly satisfied but hard to verify.
- 7–8: strong mapping from requirements to implementation.
- 9–10: highest-value criteria are undeniable in product and demo.

For non-competition products, use actual customer, market, regulatory, or operational requirements.

## C. Core vertical-slice completeness — 10

- 0–3: prototype/scaffolding only.
- 4–6: core path works with gaps/mocks.
- 7–8: real end-to-end core path works.
- 9–10: end-to-end path plus meaningful failure behavior/recovery proven.

## D. Integration depth — 10

- 0–3: decorative integration.
- 4–6: useful but replaceable.
- 7–8: platform materially improves the product.
- 9–10: platform is load-bearing to value, correctness, performance, or trust.

## E. Evidence + verifiability — 10

- 0–3: claims mostly asserted.
- 4–6: tests/logs exist but central claims remain self-reported.
- 7–8: important claims have real evidence.
- 9–10: critical claims are independently reproducible or verifiable.

## F. Failure / adversarial resilience — 10

- 0–3: happy path only.
- 4–6: basic errors handled.
- 7–8: meaningful failure classes tested.
- 9–10: realistic adversarial proof demonstrates the core protection/recovery mechanism.

## G. Measurable advantage — 10

- 0–3: value is qualitative only.
- 4–6: metrics exist but baseline/reproducibility is weak.
- 7–8: strong headline metric tied to the crux.
- 9–10: fair baseline + reproducible benchmark + memorable improvement.

## H. Engineering / production credibility — 10

- 0–3: fragile demo code.
- 4–6: reasonable implementation with obvious operational gaps.
- 7–8: appropriate testing/state/permissions/recovery/deployment discipline.
- 9–10: production qualities directly support the thesis and are visibly proven.

## I. Demo clarity + memorability — 10

- 0–3: difficult to understand or navigation-heavy.
- 4–6: understandable but generic.
- 7–8: clear problem → mechanism → result story.
- 9–10: memorable proof/failure moment + metric + clear evidence.

## J. Scope discipline + differentiation — 10

- 0–3: bloated, scattered, or indistinguishable.
- 4–6: useful but too broad/generic.
- 7–8: focused build with recognizable identity.
- 9–10: every major feature strengthens the thesis and the product stays distinct among similar SDK/model choices.

Score interpretation:

```text
90–100  Exceptional benchmark strength. Focus on polish, evidence gaps, and submission execution.
80–89   Strong. Fix the few gaps that most affect the crux or rubric.
70–79   Competitive but vulnerable. Several high-leverage weaknesses remain.
60–69   Functional build, weak competitive proof. Prioritize aggressively.
<60     Revisit the crux, vertical slice, proof, and requirement fit before adding features.
```

Do not worship the total. A high score with a fatal missing requirement can still lose.

---

# 16. Evidence grades

Classify important claims honestly:

```text
E0 — Idea only
E1 — Code/scaffolding exists
E2 — Unit/mock proof
E3 — Real local end-to-end proof
E4 — Real external/provider/hardware/network proof
E5 — Independently reproducible/verifiable proof
```

For central claims, aim for the highest practical evidence grade before submission/release.

Do not describe E2 as E4.

---

# 17. Gap prioritization

Do **not** implement every low-scoring item.

Use this mental model:

```text
Priority = Impact × Relevance × Evidence Gain × Demo Value
           -----------------------------------------------
                    Cost × Risk × Scope Creep
```

Prefer work that:

- fixes a high-weight requirement/rubric gap;
- proves the core thesis;
- turns a claim into evidence;
- creates a memorable demo moment;
- addresses a realistic failure;
- deepens a load-bearing integration;
- produces a meaningful metric;
- completes the vertical slice.

Deprioritize work that:

- merely increases feature count;
- creates infrastructure with no user/judge value;
- rewrites stable components without a proven reason;
- adds speculative scale before the core flow works;
- makes the demo longer without making the thesis clearer;
- introduces dependencies just to look sophisticated.

---

# 18. Benchmark report format for agents

When asked to compare a project against this benchmark, first inspect the actual repository, current state, relevant issues/PRs, tests, docs, live integrations/deployments, and the real competition/user requirements when accessible.

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
- Existing strengths or settled decisions that should be preserved.

## Recommended next moves
1. Highest-value action
2. Next action
3. Next action

## Demo / proof opportunity
The strongest adversarial, measurable, or independently verifiable demonstration currently available.

## Requirement / user impact
Exactly which criterion or user outcome each recommendation improves.
```

Generic advice is a failed benchmark review.

---

# 19. Rules for modifying a build after benchmarking

If asked to improve the build using this benchmark:

1. read `goated_foundation.md` if present;
2. read the target project's agent rules, current state, current sprint, requirements/rubric, and relevant architecture docs;
3. inspect actual code, tests, issues, PRs, and real integration evidence;
4. identify the highest-leverage benchmark gaps;
5. preserve settled architecture unless evidence justifies changing it;
6. convert justified improvements into bounded work with acceptance criteria;
7. implement incrementally;
8. test success and meaningful failure paths;
9. record evidence/benchmark results;
10. re-score honestly.

Do not perform a wholesale rewrite unless the current architecture fundamentally blocks the product's core claim and the evidence supports that conclusion.

---

# 20. Anti-patterns

Avoid:

- sponsor-logo integrations;
- “AI-powered” as the main differentiation;
- dashboards hiding an incomplete core workflow;
- mocked integrations presented as real;
- fake production-readiness;
- self-certifying verification with no independent check where one is practical;
- random blockchain hashes with no enforcement/user value;
- arbitrary multi-agent architectures;
- impressive test counts that do not test important claims;
- benchmark numbers with no reproducible procedure;
- security theater unrelated to the threat model;
- chasing every theoretical failure instead of meaningful ones;
- shipping ten mediocre features instead of one undeniable core mechanic;
- changing working architecture because another winner used something different;
- copying a winner's domain-specific mechanism without the underlying need.

---

# 21. Final pressure test

Before a consequential demo, launch, release, or submission, answer:

- Can a stranger explain the product after one minute?
- Is the core problem real and specific?
- Is the differentiation structural rather than cosmetic?
- Does the central workflow work end to end without hidden mocks?
- Are required sponsor/platform features genuinely load-bearing where relevant?
- What important claim are we still asking people to trust?
- Can we prove it instead?
- Is there a clear authority boundary before consequential output/action where needed?
- What realistic failure would embarrass the product during judging or production?
- Have we tested it?
- What is the memorable quantitative result, and can it be reproduced?
- What receipt/evidence remains after a successful run?
- Does the demo expose the core technical insight quickly?
- Can a judge map the product directly to the scoring rubric?
- What should we deliberately **not** add before the deadline?

---

# 22. Living benchmark protocol

This file should evolve as strong products, failures, postmortems, competition results, and winning patterns are studied.

When adding a new benchmark reference:

1. verify what the product actually built;
2. verify why it likely scored well using organizer/judge/rubric evidence where possible;
3. distinguish fact from inference;
4. extract the reusable principle;
5. avoid copying domain-specific implementation details unless they generalize;
6. add/refine a criterion only if it improves future product decisions;
7. remove stale or repetitive rules that create context bloat without predictive value.

A new winner should not automatically create a new rule.

> **Accumulate signal, not checklist length.**

---

# Invocation examples

```text
Compare our current build against goated_benchmark.md. Do not rewrite the product. Identify the highest-leverage gaps, preserve what is already strong, and tell me the smallest changes that would materially improve our proof, demo, product quality, and chances of winning.
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
