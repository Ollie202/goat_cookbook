---
name: goated-benchmark
description: Pressure-test a product against reusable patterns from strong and winning builds, then identify the smallest high-leverage improvements without bloating or destabilizing what already works.
---

# Goated Benchmark

A reusable pressure-test for making products harder to dismiss, easier to understand, more differentiated, more trustworthy, and more competitive.

Use it with `goated_foundation.md`:

- `goated_foundation.md` = **how the project is organized and executed**.
- `goated_benchmark.md` = **how strong the product itself is**.
- Keep dedicated ideation/creative-explosion material separate. This file evaluates and sharpens ideas; it should not become an idea-generator dump.

> **Accumulate signal, not checklist length.**

---

# 1. The winning thesis

Before features, answer:

> **What important thing does this product do that the obvious alternative cannot do as well?**

A strong thesis is:

- specific enough to demonstrate;
- important to a real user;
- structurally differentiated, not just differently branded;
- strengthened by the sponsor/platform rather than decorated with it;
- provable with a visible result, failure case, metric, or receipt.

Weak: `AI ad generator.`

Stronger: `The model may create the scene, but it cannot silently alter approved product assets or ship an unaudited export.`

Weak: `AI operations agent.`

Stronger: `A hallucinated diagnosis cannot directly become a destructive production action.`

Weak: `Faster media pipeline.`

Stronger: `A tiny edit should not force every expensive downstream asset to regenerate.`

If the thesis is still generic, do not hide it under more features.

---

# 2. Creative differentiation gate

The separate ideation system should generate the wild ideas. This benchmark asks whether the selected idea has **winning shape**.

Pressure-test it with four questions:

1. **Surprise** — is there a non-obvious mechanism, constraint, interaction, or failure mode that makes the build memorable?
2. **Necessity** — does that mechanism solve a real problem rather than exist for novelty?
3. **Demonstrability** — can a stranger see why it matters in under a minute?
4. **Defensibility** — if ten teams use the same SDK/models, is this still recognizably ours?

Prefer **mechanism-level differentiation** over feature-count differentiation:

- a protected boundary;
- independent verification;
- deterministic recovery;
- a novel state transition;
- meaningful cross-system coordination;
- cost/latency collapse;
- local/offline execution;
- adversarial resistance;
- a new way of composing sponsor primitives into a real user outcome.

Do not copy a winner's mechanism unless the underlying problem genuinely requires it.

---

# 3. Treat the rubric as a product requirement

For hackathons, competitions, grants, sponsor tracks, and platform challenges, determine:

- exact judging criteria and weights;
- required vs optional capabilities;
- what must be real rather than mocked;
- disqualifiers;
- what the sponsor is actually trying to showcase;
- what evidence a judge can inspect independently.

Maintain a compact map:

| Criterion | Weight | Implementation | Demo moment | Evidence |
|---|---:|---|---|---|
| Example | 30% | `packages/...` | 01:20 | test / URL / tx / hash |

A judge should never have to reverse-engineer the repo to award points.

---

# 4. Make sponsor technology load-bearing

Bad:

```text
Generate thing → upload to sponsor → show sponsor logo
```

Strong:

```text
Remove sponsor primitive → product loses correctness, performance,
trust, economics, execution capability, or core user value.
```

Ask:

> **If the sponsor/platform disappeared, what important capability would break?**

Good integrations include storage used for integrity/retrieval guarantees, chains used for settlement/enforcement/shared state, agent frameworks used for real orchestration or tool execution, and hardware used for measurable privacy/latency/offline/cost advantages.

Decorative integration is usually visible immediately.

---

# 5. Separate creativity/reasoning from authority

When AI or probabilistic systems are involved:

```text
MODEL PROPOSES / GENERATES / REASONS
                ↓
POLICY / DETERMINISTIC CHECK / SOURCE-OF-TRUTH VALIDATION
                ↓
AUTHORIZED EXPORT / EXECUTION / TRANSFER / DEPLOYMENT
```

> **Generation is not permission to ship. Reasoning is not permission to act.**

For each consequential path, decide:

- what may be creative;
- what must stay exact;
- what must be independently grounded;
- what must fail closed;
- what action is irreversible or financially meaningful.

Use the simplest boundary that protects the real invariant. Do not add cryptography, consensus, human approval, or policy engines as theater.

---

# 6. Finish the real vertical slice first

Prefer:

```text
real user input
→ real core mechanic
→ real sponsor/provider path where required
→ real persisted/executed result
→ real failure behavior
→ real evidence
→ polished demo
```

before speculative dashboards, marketplaces, extra agents, microservices, integrations, enterprise settings, or decorative analytics.

The best next feature is often the one that makes the core claim more undeniable.

---

# 7. Build a proof ladder, not a vanity test count

For every central claim, climb as high as practical:

```text
E0 — idea only
E1 — implementation/scaffolding exists
E2 — unit/mock proof
E3 — real local end-to-end proof
E4 — real external/provider/hardware/network proof
E5 — independently reproducible/verifiable proof
```

Do not describe E2 as E4.

Testing should cover the product's claims, not merely lines of code:

- happy path;
- malformed/missing input;
- realistic provider/network failure;
- stale/duplicated/tampered state when relevant;
- core security/trust invariant;
- deterministic/reproducible behavior where claimed;
- clean-checkout or fresh-environment execution;
- the exact path used in the demo.

For important workflows, keep a **golden fixture** that can reproduce both success and at least one meaningful refusal/failure path.

---

# 8. Failure → invariant → permanent protection

Do not patch meaningful failures once.

```text
FAILURE
  ↓
GENERAL FAILURE CLASS
  ↓
INVARIANT
  ↓
TEST / GUARD / AUDIT / STATE MACHINE
  ↓
REGRESSION PROTECTION
```

A bug that teaches something should improve the long-term system.

Example:

```text
A font silently renders empty glyphs
→ required characters are not guaranteed by the chosen font
→ invariant: every rendered character must exist before export
→ glyph-coverage audit + blocking test
```

---

# 9. Replace important trust with receipts

Ask of every important claim:

> **What is the receipt?**

A useful receipt may contain:

- content/input hashes;
- source revision;
- transaction/deployment/storage IDs;
- execution trace;
- model/version/seed where relevant;
- audit observations and thresholds;
- benchmark output;
- test run;
- timestamps;
- provenance/export manifest;
- independently retrieved/recomputed state.

Weak: `Verified ✅`

Strong: `Verified against source X, bytes Y, recomputed value Z, with the exact audit result recorded.`

The more consequential the claim, the less it should depend on a decorative badge.

---

# 10. Independently verify critical state

When practical, do not let the same component both make a critical claim and be the only evidence that it is true.

Ask:

> **If every internal status field incorrectly said “success,” how would we catch it?**

Examples:

- retrieve and hash stored bytes instead of trusting a DB row;
- query the real network/provider instead of trusting a deployment report;
- recompute an output rather than trusting a UI badge;
- validate model output deterministically where possible;
- compare two independent evidence sources when one can drift or lie.

---

# 11. Turn the headline into a number

Strong products often compress their advantage into one memorable measurement.

Examples:

```text
18 nodes total
4 rebuilt
14 reused
10 provider calls avoided
```

```text
Cold: 71.7s
Warm: 45.4s
90/90 blocking checks passed
0 outbound connections
```

A good metric is:

- tied directly to the thesis;
- measured on the real system;
- compared against a fair baseline when useful;
- reproducible;
- explicit about environment/fixture;
- hard to inflate with vanity statistics.

Preserve the benchmark as:

```text
checked-in command + fixture + environment + raw result + summary + caveats
```

Never fabricate precision or cherry-pick a deliberately weak baseline.

---

# 12. Engineer the demo before the final day

The demo is part of the product.

A strong short demo should answer, fast:

1. What hurts?
2. Why does the obvious approach fail?
3. What is our non-obvious mechanism?
4. Where is the sponsor/platform load-bearing?
5. What is the **one memorable moment**?
6. What number proves the claim?
7. What happens when it breaks or is attacked?
8. What evidence remains afterward?

Recommended arc:

```text
PROBLEM
→ OBVIOUS FAILURE
→ CORE MECHANIC
→ LIVE SUCCESS
→ REALISTIC FAILURE / TAMPER
→ DETECTION / REFUSAL / RECOVERY
→ HEADLINE METRIC
→ RECEIPT / EVIDENCE
```

Do not spend a short judging video clicking through navigation.

## Demo/video proof path

Before submission, maintain one compact `demo-plan.md` (or equivalent) containing:

```text
HOOK — 10–20s: problem + one-sentence thesis
SETUP — minimal input/context
LIVE PATH — prove the core mechanic end to end
WOW MOMENT — the thing judges will remember
FAILURE PATH — tamper/bad model/provider failure where meaningful
PROOF — metric + receipt + real integration evidence
CLOSE — why this matters + sponsor fit
```

Also maintain:

- exact demo fixture/input;
- exact commands/URLs/accounts needed;
- expected outputs;
- fallback recording path if live infrastructure fails;
- clean-screen/rehearsal checklist;
- video time budget;
- final submission links tested from a logged-out/private browser.

The recorded video should show **real execution**. If footage is sped up, simulated, cached, or prerecorded, disclose it clearly rather than creating misleading evidence.

---

# 13. Submission-ready proof bundle

A winning build should be easy to verify after the pitch.

Where appropriate, ship:

```text
README: thesis + 60-second verification path
live demo: fastest way to experience value
video: judge-compressed story
benchmark: reproducible headline metric
fixture: known input for success/failure
receipt/evidence: output proving what happened
submission-check: secrets, links, licenses, required files
```

The repository, demo, and video should tell the same story.

---

# 14. Production credibility should support the thesis

Production-readiness is not “add Kubernetes.”

Only invest in operational qualities that matter to the product or rubric:

- retries/idempotency;
- recovery/reconciliation;
- observability;
- secrets/permissions;
- durable state;
- concurrency/rate limits;
- deployment reproducibility;
- user-facing failure states;
- safe handling of irreversible actions.

Make relevant qualities visible in the demo/evidence when they are scored.

---

# 15. Winner-pattern references

These are **generalized lessons, not architectures to copy**.

## Rivet — bounded creativity + enforced export boundary

Verified from the public build: protected product/logo/text assets route around the generative path; exports are blocked by named audits; a Campaign Receipt records hashes, timings, audit observations and repairs; the repo exposes reproducible test/benchmark commands and demonstrates both a verified campaign and a tampered/refused one.

Reusable lessons:

> **Use models where variability helps; deterministic controls where correctness matters.**

> **A refusal can be as compelling as a success when it proves the product's core promise.**

> **Make the strongest claim reproducible from the repository, not only visible in a polished UI.**

## TakeGraph-style — incremental work + independent correctness

Reusable lessons:

- model expensive work as dependencies;
- rebuild only invalidated work;
- fingerprint the things you reuse;
- verify reuse against real stored state;
- explain why work was reused/rebuilt;
- measure avoided work;
- turn discovered inconsistencies into canonical invariants.

> **Optimization becomes credible when it is deterministic, measurable, externally checked, and explainable.**

## Backstop-style — reasoning is not authority

Reusable lessons:

- AI proposes diagnosis/action;
- real signals ground it;
- deterministic guardrails decide whether execution is permitted;
- unsafe model conclusions are intentionally demonstrated and blocked.

> **The strongest agent demos often prove what the agent is prevented from doing, not only what it can do.**

## On-chain / cross-source integrity patterns

> **Use decentralized infrastructure when independent enforcement or shared verifiable state is part of the product, not as decorative provenance.**

> **When one evidence source can drift or lie, cross-verification can turn weak telemetry into a stronger integrity claim.**

---

# 16. Goated scorecard — 100 points

Score what materially applies; mark irrelevant dimensions `N/A` rather than inventing work.

| Dimension | Points | 9–10 quality looks like |
|---|---:|---|
| Problem + thesis | 10 | memorable, important, demonstrable crux |
| Rubric/user fit | 10 | highest-value requirements are undeniable |
| Vertical slice | 10 | real E2E path + meaningful failure behavior |
| Integration depth | 10 | sponsor/platform is load-bearing |
| Evidence | 10 | central claims are independently reproducible/verifiable |
| Failure resilience | 10 | realistic adversarial/failure proof exists |
| Measurable advantage | 10 | fair reproducible headline metric |
| Engineering credibility | 10 | production qualities support the thesis |
| Demo memorability | 10 | clear mechanism + wow moment + proof |
| Scope + differentiation | 10 | focused, structurally distinct, no feature bloat |

Interpretation:

```text
90–100  Exceptional: polish proof and submission execution.
80–89   Strong: fix the few highest-leverage gaps.
70–79   Competitive but vulnerable.
60–69   Functional, weak competitive proof.
<60     Revisit thesis, vertical slice, proof, or requirement fit.
```

A fatal missing requirement can still lose with a high total.

---

# 17. Gap prioritization

Do not implement every low score.

```text
Priority = Impact × Relevance × Evidence Gain × Demo Value
           -----------------------------------------------
                    Cost × Risk × Scope Creep
```

Prefer work that proves the thesis, closes a high-weight rubric gap, deepens a load-bearing integration, creates a memorable demo moment, converts trust into evidence, or produces a defensible metric.

Deprioritize work that merely adds features, infrastructure, agents, dashboards, dependencies, or speculative scale.

---

# 18. Benchmark review format

When asked to benchmark a repo, inspect the actual implementation, current state, issues/PRs, tests, live integrations, and current competition requirements before scoring.

Return:

```markdown
# Goated Benchmark Review

## Product thesis
One sentence.

## Current score
XX/100

## What is already strong
Evidence-backed strengths.

## Highest-leverage gaps
For each: why it matters, evidence level, smallest strong fix, cost/risk.

## Do NOT change
Strengths/settled decisions to preserve.

## Recommended next moves
Only the highest-value actions.

## Demo/proof opportunity
The strongest memorable success + failure + metric + receipt path.

## Requirement impact
Which criterion/user outcome each move improves.
```

Generic advice is a failed benchmark review.

---

# 19. Final pressure test

Before a consequential submission/release:

- Can a stranger explain it after one minute?
- Is the thesis specific and structurally differentiated?
- Does the core path work end to end without hidden mocks?
- Is the sponsor/platform genuinely load-bearing?
- What central claim still depends on trust instead of proof?
- Have we tested the failure most likely to embarrass us?
- Can we demonstrate that failure safely?
- What is the one memorable metric?
- Can it be reproduced?
- What receipt remains after execution?
- Does the demo expose the technical insight quickly?
- Do README, live app, video, evidence, and rubric map tell one coherent story?
- What should we deliberately **not** add before the deadline?

---

# 20. Living benchmark protocol

When studying another winner:

1. verify what was actually built;
2. verify the rubric/judge context when available;
3. separate fact from inference;
4. extract the reusable mechanism;
5. strengthen an existing rule before adding a new one;
6. delete repetition created by the update;
7. never turn this file into a museum of winners.

> **A new winner should improve our judgment, not increase our token bill.**

---

# Invocation examples

```text
Compare this repo against goated_benchmark.md and the real hackathon rubric. Preserve what already works. Verify implementation before scoring, rank only the highest-leverage gaps, and do not recommend feature bloat.
```

```text
Benchmark this build, then turn only the top three justified improvements into bounded issues with acceptance criteria and a concrete demo/proof path.
```

```text
Re-score after the latest milestone. Show which claims moved up the evidence ladder, what still depends on trust, and the single demo moment most likely to make the product difficult to dismiss.
```
