---
name: goated-research
description: Research hackathons and product opportunities before coding by extracting official requirements, sponsor intent, winner patterns, saturation, dependencies, buildability, and demoability so agents produce differentiated, feasible directions instead of generic brainstorms.
---

# Goated Research

A reusable pre-build research system for hackathons, sponsor challenges, grants, and time-bounded product builds.

> **Do not begin with an idea. Begin with what the event rewards, what the sponsor wants proven, what users will care about, what has already been built, and what we can actually ship — then derive the idea.**

Use the cookbook in this order:

```text
goated_research.md   → What is worth building, and why?
goated_foundation.md → How do we structure and execute it?
goated_benchmark.md  → How strong is the working product, and what should improve?
```

This file does **not** prescribe one winning architecture. A simple consumer experience can be the right answer; so can a deep infrastructure primitive. **Complexity must be earned by the rubric, user problem, or core mechanism.**

---

# 1. What good research must answer

Before serious implementation, a fresh agent should know:

- the real rules, build period, deliverables, disqualifiers, and judging criteria;
- what the sponsor is actually trying to prove, grow, or get builders to adopt;
- what relevant winners and prior projects already did;
- which categories are crowded or obvious, and where negative space exists;
- who the target user is and the specific moment in which the product matters;
- which sponsor capabilities can be naturally load-bearing;
- whether a solo builder can finish the core in time;
- which APIs, data, credits, testnets, hardware, accounts, or approvals can kill the idea;
- what the real end-to-end demo looks like;
- what must be de-risked before a large codebase exists.

If research ends with twenty vague ideas and no recommendation, it failed.

---

# 2. Research rules

## Evidence before ideation

Do not brainstorm from the hackathon title alone. First inspect the event, sponsor, ecosystem, winners, and constraints.

These are common defaults, not forbidden categories:

```text
generic chatbot / generic AI agent
generic trading bot / prediction market
generic DeFi aggregator / NFT marketplace
generic dashboard / social feed / data visualizer
```

A common category is fine only when it has a specific wedge in mechanism, workflow, UX, distribution, economics, timing, or sponsor-native capability.

Do not assume:

```text
Web3 = DeFi protocol
AI = multi-agent system
sports = prediction market
agent hackathon = chatbot with tools
storage = upload a file
hardware = biggest possible model stack
```

## Copy principles, not products

From winners, extract **problem framing, core mechanic, sponsor fit, demo, measurement, and scope discipline**. Do not transplant domain-specific architecture into unrelated builds.

## Mark confidence

```text
FACT      — directly supported by an authoritative source or working artifact
INFERENCE — conclusion drawn from facts; not judge testimony
IDEA      — proposed direction
UNKNOWN   — unresolved information
BLOCKER   — unresolved fact capable of killing qualification or the demo
```

## Completion beats fantasy

Prefer a narrow, real vertical slice over a giant roadmap. Research should prevent discovering late that the critical API is private, the faucet is dead, the data is unavailable, the model is unaffordable, or the core cannot be demonstrated.

---

# 3. Source hierarchy

Prefer, in order:

1. official rules, challenge page, rubric, eligibility terms;
2. official sponsor docs, SDKs, starter repos, FAQs, blog/forum updates;
3. official winner announcement or judge/organizer postmortem;
4. winner submission, source repo, README, demo, tests, benchmarks, evidence;
5. sponsor engineers, public support threads, GitHub issues/discussions;
6. high-quality third-party analysis;
7. social mirrors/search snippets only when originals are inaccessible, clearly labelled.

For technical claims, inspect the actual docs/SDK/repository. For winners, a congratulatory post is only the entry point: inspect the build whenever possible.

---

# 4. Hackathon Truth Sheet

Resolve this before serious ideation:

```text
Hackathon / organizer / sponsors
Dates + actual build period + time remaining
Solo/team rules
Prize structure
Tracks
Required technology / network / hardware
Required deliverables
Demo format / recommended or maximum length
Judging criteria + weights
Usage / transaction / onchain requirements
Existing-project rules
Social/community requirements
Geographic/KYC restrictions if relevant
Disqualifiers
Free credits / hardware / faucet / testnet
Submission method
```

Source every consequential item.

Then write one explicit inference:

> **To win this event, a project most likely needs to demonstrate __________.**

---

# 5. Extract the sponsor thesis

The rules say what is allowed. Sponsor behavior often reveals what matters.

Research:

- the product/infrastructure the sponsor is currently pushing;
- new SDKs, protocols, chains, models, hardware, marketplaces, or APIs they want adopted;
- capabilities their docs/blogs repeat: speed, privacy, transactions, interoperability, durability, local inference, agent autonomy, etc.;
- usage they can actually measure: transactions, API calls, users, uploaded data, marketplace listings, revenue, performance;
- common platform friction and what the sponsor already solves;
- free credits/testnets/hardware and realistic developer access.

Key question:

> **What successful demo would make the sponsor say, “This is a strong reason our technology should exist or be used”?**

Sponsor-native does not mean using every feature. Use what materially strengthens the product.

---

# 6. Winner archaeology + saturation

Study roughly 3–10 relevant winners when enough evidence exists: same event first, then prior seasons and comparable sponsor/category events.

Capture only:

| Field | What to learn |
|---|---|
| Placement | Is the result officially verified? |
| Product + user | What did it do, for whom? |
| Core mechanic | What made it more than the obvious version? |
| Sponsor fit | Why did the platform matter? |
| Demo | What could judges visibly see happen? |
| Evidence | What measurable/inspectable result existed? |
| Scope | What was genuinely necessary? |
| Likely rubric fit | Which scored dimensions did it attack? Mark inference. |
| Reusable lesson | What transfers to unrelated builds? |
| Do not copy | What was domain-specific? |

Then find negative space:

- repeated/crowded categories;
- ignored users or workflows;
- underused sponsor primitives;
- awkward experiences around otherwise-good infrastructure;
- things newly possible because the ecosystem changed;
- ideas that winners validate but did not fully explore.

Never reason: **winner used X → we need X**.

---

# 7. Generate opportunities across different shapes

Force diversity before ranking so every brainstorm does not collapse into DeFi, infrastructure, or agents.

```text
USERS
consumer/fan · creator · operator/business · developer · community
trader/participant · agent · agent developer · institution

VERBS
create · watch · play · coordinate · pay · trade · verify · learn
choose · automate · recover · share · compete

TIMING
before live event · during live event · after event
recurring workflow · urgent one-shot · background autonomous workflow

PRODUCT SHAPES
delightful consumer app · social/multiplayer · game/competition
vertical workflow · developer tool · infrastructure primitive
marketplace/coordination · agent-native service · creative tool

SPONSOR PRIMITIVES
compute · storage/data · payment/settlement · identity/reputation
memory/provenance · market/liquidity · orchestration · interoperability
security/verification
```

A serious idea slate should normally include **at least three product shapes** before selection.

For each opportunity, answer:

> **Who is doing what, at what moment, and what fails or remains painful without us?**

If this cannot be made specific, the idea is not ready.

---

# 8. Buildability + dependency gate

Our low-friction default stack, when compatible:

```text
Vercel   → frontend / web
Railway  → APIs, workers, persistent backend processes
Supabase → Postgres, auth, storage/realtime only when needed
GitHub   → source, CI, issues/PRs, evidence
```

Do not add Redis, Kafka, Kubernetes, vector databases, multiple chains, or many model providers unless they earn their existence.

Prefer official sponsor SDKs/testnets, public/free APIs, sponsor credits, generous free tiers, and open data. Identify material external spend before selecting the idea.

For every critical dependency ask:

```text
Can we access it now?
Does it require approval/waitlist?
Is a sandbox/testnet/faucet available?
Can we make one real call today?
Is the SDK current and documented?
What are free-tier/rate-limit/demo costs?
Does it require unavailable paid hardware?
Is the needed data actually accessible and licensed?
Will auth/CORS/region constraints affect deployment?
Can it run in the judging environment?
What happens if it fails during the demo?
```

The core sponsor integration must be real. Non-core dependencies may have honest deterministic fallbacks when useful.

### Kill / pivot early when

- the central API/hardware/network cannot be accessed or proven in time;
- the demo depends on expensive/unavailable data or manual approval;
- the idea becomes interesting only after features we cannot finish;
- sponsor integration remains decorative;
- the real-world value cannot be shown in a short end-to-end demo;
- operational surface is clearly too large for the deadline.

A killed idea is cheaper than a half-built submission.

---

# 9. Demo-first idea test

Before selecting a direction, write the demo in plain English.

```text
0–10s   real situation / user problem
10–25s  real input
25–50s  core mechanic + sponsor/platform interaction
50–70s  consequential output/action
70–90s  visible result: transaction, artifact, saved work, recovered failure,
        better experience, measurable outcome, or evidence
```

The arc must fit the product. A fun consumer app does not need a security failure demo; verification infrastructure probably does.

Ask:

- what one screenshot or 10-second clip explains why this is interesting?
- can the product produce it for real?
- can judges understand the use case without an architecture lecture?
- does sponsor technology visibly matter?

If the best moment only exists in the roadmap, the idea is weak.

---

# 10. Calibrate complexity: reference patterns

These are reminders that different rubrics reward different product shapes.

## X Cup — consumer/market-first

The World Cup-themed X Cup allowed prediction, trading, social, NFT, GameFi, and AI-agent products, while judging differentiation, market potential, completion/demonstrability, and onchain verifiability.

Winners were varied:

- **Billion Live — 1st:** livestream/social trading with one-tap copy actions inside the stream;
- **ShieldSuite — 2nd:** yield-backed player speculation plus AI trading;
- **WorldXI — 2nd:** onchain fantasy squad with real-match scoring;
- **Choice Market — 3rd:** turns trending topics/debates into tradeable markets;
- **CupFolio — 3rd:** AI-managed World Cup prediction portfolio;
- **Polygoal — 3rd:** World Cup prediction market with onchain settlement.

Lesson:

> **When market potential, engagement, creativity, and completion matter, a sticky consumer loop can beat a technically heavier protocol. Technical complexity is not product strength.**

Reference: `https://web3.okx.com/xlayer/build-x-hackathon/xcup`

## Rivet — deep vertical workflow

Rivet won AMD's multimodal track with a local ad workflow: Radeon/ROCm handled the real multimodal workload; protected assets stayed outside generative authority; outputs were audited before export; performance and reproducibility were measured.

Lesson:

> **When functional completeness and platform performance are central, go deep on one workflow and make the sponsor technology visibly responsible for the result.**

References: `https://github.com/damishafe/Rivet` · `https://github.com/AMD-DEV-CONTEST/Radeon-hackathon-2026-07/pull/237`

## TakeGraph — infrastructure as product

TakeGraph treated generative media as a dependency graph with selective rebuilds, provider recovery, content-addressed Backblaze B2 storage, and re-verifiable releases — appropriate for a challenge emphasizing production readiness, storage/orchestration, and generative media infrastructure.

Lesson:

> **Infrastructure is a strong bet when the sponsor/rubric explicitly rewards reliability, orchestration, storage, performance, or developer primitives. It is not the default for every hackathon.**

References: `https://github.com/Enoch208/takegraph` · `https://backblaze-generative-media.devpost.com/`

## Agent-economy pattern

Do not stop at “agent that performs task X.” Research what becomes necessary when software can operate, pay, coordinate, own state, hire services, build reputation, or make decisions autonomously:

```text
payments · budgets/credit · reputation · identity · memory
coordination · permissions · discovery · settlement · accountability · recovery
```

Lesson:

> **Ask what new primitive or workflow autonomy creates, then check whether the hackathon actually rewards that depth.**

The examples are reference points, not products to copy.

---

# 11. Produce five serious concepts, then rank them

Generate roughly **five serious concepts**, not thirty filler ideas. Each must include:

```text
Working name
Target user + specific real-world moment
One-sentence crux
Core mechanic
Natural sponsor/platform role
Why it is not the generic version
60–90 second demo
Minimum complete vertical slice
Required APIs/SDKs/data/testnet/models
Likely cost
Biggest blocker
Explicit non-goals
Why it could score against the actual rubric
```

At least one concept should normally be simpler than the first instinct, and the slate should span multiple product shapes when the event permits.

Research-stage scoring is 1–5, not the `goated_benchmark.md` 100-point score:

| Dimension | Question |
|---|---|
| Rubric leverage | Does it attack high-value criteria? |
| Sponsor fit | Is sponsor tech naturally important? |
| User clarity | Is the real use case immediately understandable? |
| Differentiation | Is there a concrete wedge? |
| Buildability | Can a solo builder finish the core? |
| Demo potency | Can the value be shown quickly and for real? |
| Dependency safety | Are APIs/data/credits/hardware accessible and affordable? |

Also record:

```text
Fatal blocker? YES / NO
Complexity tax: LOW / MEDIUM / HIGH
```

Complexity is not a bonus. Every extra service, chain, model, contract, agent, or queue must buy user value, rubric leverage, or demo value.

---

# 12. P0 de-risking before serious coding

After choosing a direction, immediately prove the riskiest assumptions:

- make the smallest real SDK/API call;
- deploy/read a tiny test contract;
- verify faucet/credits/hardware access;
- run the required model;
- fetch the real data;
- perform one sponsor-native transaction;
- test auth/CORS from the intended environment;
- prove the hardest transformation with a fixture;
- confirm the intended demo can actually capture the result.

Do not polish the UI before testing what can kill the project.

Once P0 survives, use `goated_foundation.md` for milestones and execution.

---

# 13. Agent output contract

When asked:

```text
Research what we can build for <hackathon> using goated_research.md.
```

Return:

```markdown
# Hackathon Research

## Verified Hackathon Truth
Rules, dates, deliverables, rubric, constraints, required tech, build period — cited.

## Sponsor Thesis
What the sponsor appears to want demonstrated/adopted. Separate FACT from INFERENCE.

## Winner + Prior-Art Archaeology
Relevant builds, core mechanics, sponsor fit, demos, and reusable lessons.

## Saturated / Weak Default Zones
Likely common submissions and what would make those categories non-generic.

## Opportunity Map
Underserved users, moments, product shapes, and sponsor primitives.

## Build Constraints + Dependency Reality
APIs, SDKs, data, hardware, testnets, credits, cost, approvals, blockers.

## Five Serious Concepts
User, crux, mechanic, sponsor fit, differentiation, MVP, dependencies,
cost, demo, non-goals, rubric fit.

## Top Three Comparison
1–5 research-stage scores + fatal blockers + complexity tax.

## Recommended Direction
One primary recommendation, why it is the best risk-adjusted bet,
and what evidence would make us abandon it.

## P0 De-risking Checks
Smallest real experiments before serious implementation.
```

Do not conclude that every idea is equally good. Make a recommendation.

Do not start a full repository/build unless the user asks to proceed.

---

# 14. Stop research before it becomes bloat

Stop the initial pass when we know:

- the consequential rules/disqualifiers;
- the sponsor thesis;
- what relevant winners actually did;
- obvious crowded categories;
- at least three credible opportunity directions;
- the best risk-adjusted direction;
- whether its critical dependencies are accessible enough for a P0 spike.

Then test the riskiest assumption. Return to research when new evidence changes the decision.

This global file stores **method and durable cross-hackathon signal**, not every project ever researched. Detailed event research belongs in the target project's `research/` docs.

When a new winner teaches something:

```text
new opportunity/research lesson    → refine goated_research.md
project organization/execution     → goated_foundation.md
working-product quality/pressure   → goated_benchmark.md
```

Only change the global file when the new lesson is genuinely durable.

> **Accumulate starting advantage, not context bloat.**

---

# Invocation examples

```text
Research what we can build for this hackathon using goated_research.md from goat_cookbook. Start from the official rules, sponsor intent, winners, ecosystem, and dependency reality — not generic ideation. Give me five serious concepts, compare the top three, and recommend the strongest one.
```

```text
Use goated_research.md to pressure-test this idea before we build it. Verify the critical APIs/testnet/data/credits, show me the 90-second real demo, identify what can kill the project, and recommend continue or pivot.
```
