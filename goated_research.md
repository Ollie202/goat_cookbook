---
name: goated-research
description: Research hackathons and product opportunities before coding by extracting official requirements, sponsor intent, winner patterns, saturation, dependencies, buildability, and demoability so agents generate a small set of differentiated, feasible ideas instead of starting from generic brainstorms.
---

# Goated Research

A reusable research operating system for hackathons, sponsor challenges, ecosystem grants, and time-bounded product builds.

Core principle:

> **Do not begin with an idea. Begin with what the event rewards, what the sponsor wants proven, what users will care about, what has already been built, and what we can actually ship — then derive the idea.**

This file is deliberately different from the other cookbook skills:

```text
goated_research.md
→ What is worth building, and why?

        ↓ chosen direction

goated_foundation.md
→ How do we structure and execute the project without agent drift?

        ↓ working product

goated_benchmark.md
→ How strong is the actual build, and what should materially improve?
```

Do not use `goated_research.md` to force every project into the same architecture. A winning consumer app may be conceptually simple. A winning infrastructure project may be technically deep. **Complexity must be earned by the hackathon, the user problem, or the core mechanism.**

---

# 1. Research outcome

Good research should let a fresh agent answer, before serious implementation:

- What exactly is this hackathon asking for?
- What is explicitly scored, required, optional, or disqualifying?
- What is the sponsor actually trying to make builders prove or adopt?
- What kinds of projects have already won here or in comparable events?
- What categories are crowded, obvious, or overused?
- Where is the negative space?
- Which users and real-world moments are naturally relevant?
- Which sponsor primitives can become useful parts of a product rather than decorative integrations?
- What can a solo builder realistically finish in the available time?
- What external APIs, credits, hardware, testnets, data, accounts, or approvals are required?
- Can the core value be demonstrated clearly in a short video using a real end-to-end flow?
- What should be de-risked before we create a large codebase?

If the research ends with twenty vague ideas and no clear recommendation, it failed.

---

# 2. Research rules

## Start with evidence, not brainstorming

Do not immediately generate product ideas from the hackathon title.

First inspect the real event, sponsor, ecosystem, prior art, and constraints. Generic brainstorming before this step tends to produce the same defaults:

- generic chatbot;
- generic AI agent;
- generic trading bot;
- generic prediction market;
- generic DeFi aggregator;
- generic NFT marketplace;
- generic dashboard;
- generic social feed;
- generic data visualizer.

These categories are **not banned**. They simply do not deserve to be the default. A common category is acceptable when the build has a real wedge in mechanism, workflow, user experience, distribution, economics, timing, or sponsor-native capability.

## Match the event instead of our favorite architecture

Do not assume:

```text
Web3 hackathon = DeFi protocol
AI hackathon = multi-agent system
hardware hackathon = giant model stack
storage hackathon = upload a file
agent hackathon = chatbot with tools
sports hackathon = prediction market
```

The correct product shape comes from the actual opportunity.

## Copy principles, not products

When studying winners, extract:

- why the problem framing worked;
- what mechanic made the product memorable;
- how the sponsor technology mattered;
- what the demo proved;
- what was measured;
- how much surface area was actually necessary.

Do **not** copy a winner's domain-specific architecture into an unrelated build.

## Separate fact from inference

Use these labels in serious research:

```text
FACT       — directly supported by an authoritative source or working artifact
INFERENCE  — conclusion drawn from facts; useful but not judge testimony
IDEA       — proposed direction, not yet validated
UNKNOWN    — unresolved information
BLOCKER    — unresolved fact that can prevent the idea from working or qualifying
```

Do not present “why this project won” as a fact unless judges or organizers actually explained why.

## Completion beats fantasy

A narrow product with a real user input, real core mechanic, real sponsor integration, real output, and strong demo is usually a better hackathon bet than a huge roadmap with five unfinished systems.

Research should reduce the chance that we discover on day six that the critical API is private, the faucet does not work, the model costs too much, the data does not exist, or the product cannot be demonstrated.

---

# 3. Source hierarchy

Prefer sources in this order:

1. **Official rules / challenge page / judging rubric / eligibility terms**
2. **Official sponsor docs, SDKs, example repos, blog posts, forum updates, starter kits, FAQs**
3. **Official winner announcement or judge/organizer postmortem**
4. **Winner submission page, source repository, demo video, benchmark/evidence artifacts**
5. **Sponsor engineers, ecosystem team posts, public support threads, GitHub issues/discussions**
6. **High-quality third-party analysis**
7. **Social mirrors / search snippets**, only when the original is inaccessible and labelled accordingly

For technical questions, inspect the actual SDK/docs/repository rather than trusting marketing summaries.

For a winning project, the congratulatory post is only the start. Whenever possible inspect:

```text
submission
+ source repo
+ README
+ architecture
+ demo
+ tests / benchmarks
+ evidence
+ organizer comments
```

That is where the reusable signal usually lives.

---

# 4. Build the Hackathon Truth Sheet first

Before ideation, resolve the following as far as possible:

```text
Hackathon:
Organizer / sponsor:
Dates / actual build period:
Time remaining:
Solo/team rules:
Prize structure:
Eligible tracks:
Required technology:
Required deployment/network/hardware:
Required deliverables:
Demo format + maximum/recommended length:
Judging criteria + weights:
Onchain / usage / transaction requirements:
Existing-project rules:
Social/community requirements:
Geographic/KYC restrictions if relevant:
Disqualifiers:
Free credits / hardware / faucet / testnet support:
Submission method:
Winner announcement timing:
```

Every important claim should have a source.

Then write one sentence:

> **To win this event, a project most likely needs to demonstrate __________.**

This is an inference, not scripture, but it forces the research into a usable thesis.

---

# 5. Extract the sponsor thesis

A hackathon page tells us the rules. Sponsor behavior tells us what they care about.

Research:

- what product/infrastructure the sponsor is currently pushing;
- what new SDK, chain, protocol, model, hardware capability, marketplace, or API they want adoption for;
- what their official examples demonstrate;
- which product qualities their docs/blogs repeat: speed, privacy, interoperability, transactions, agent autonomy, storage durability, local inference, etc.;
- what usage they can actually measure: transactions, API calls, uploaded data, marketplace listings, revenue, active agents, users, model performance;
- what common developer friction exists around the platform;
- what complimentary tooling is already supplied so we do not rebuild it badly;
- what free credits/testnets/hardware are available.

Key question:

> **What successful demo would make the sponsor say: “This is a strong reason our technology should exist or be used”?**

Sponsor-native does not mean “use every sponsor feature.” Use the capabilities that materially improve the product.

---

# 6. Winner archaeology

Study roughly 3–10 relevant winners when enough evidence exists. Prefer the same hackathon, then prior seasons, then comparable sponsor/category events.

For each useful reference, capture only this:

| Field | Question |
|---|---|
| Placement | Was the win officially verified? |
| Product | What did it do in one sentence? |
| User | Who actually benefits? |
| Core mechanic | What made it more than the obvious version? |
| Sponsor fit | Why did the platform matter? |
| Demo moment | What could a judge see happen? |
| Evidence | What measurable/inspectable result existed? |
| Complexity | What was genuinely necessary vs decorative? |
| Likely rubric fit | Which scored dimensions did it attack? Mark inference as inference. |
| Reusable lesson | What principle transfers to unrelated projects? |
| Do not copy | What was domain-specific? |

After several winners, look for **negative space**:

- which ideas repeat constantly;
- which user groups nobody serves;
- which sponsor capabilities are underused;
- which workflows are awkward despite strong primitives;
- what only became possible recently;
- what existing winners prove is viable but leave incomplete;
- which idea class is now too obvious unless we have a new mechanism.

Do not conclude “winner used X, therefore we need X.”

---

# 7. Use multiple product shapes when generating opportunities

Before choosing an idea, deliberately explore different shapes so every brainstorm does not collapse into the same type of app.

Useful dimensions:

### Users

```text
consumer / fan
creator
operator / business
developer
community
trader / participant
agent
agent developer
institution
```

### User verbs

```text
create
watch
play
coordinate
pay
trade
verify
learn
choose
monitor
automate
recover
share
compete
```

### Timing

```text
before an event
during a live event
after an event
recurring workflow
one-shot urgent workflow
background autonomous workflow
```

### Product shapes

```text
delightful consumer experience
social / multiplayer loop
game / competition
practical vertical workflow
developer tool
infrastructure primitive
marketplace / coordination layer
agent-native service
creative tool
```

### Sponsor primitives

```text
compute / hardware
storage / data
payments / settlement
identity / reputation
memory / provenance
market / liquidity
agent tools / orchestration
messaging / interoperability
security / verification
```

A serious idea slate should normally include **at least three different product shapes** before ranking. This is how we avoid deciding in advance that every Web3 project must be DeFi or every agent project must be infrastructure.

---

# 8. Real-world use-case gate

For every serious idea, identify a specific moment where somebody would actually use it.

Weak:

> Football fans need more engagement.

Stronger:

> A viewer is already watching a live match and wants to act on a friend's/trader's conviction without leaving the stream or reconstructing the action manually.

Weak:

> AI ads need safety.

Stronger:

> A small merchant is about to publish dozens of generated ads without a legal/brand reviewer and needs the tool to stop an unapproved claim or altered product before export.

Weak:

> Agents need trust.

Stronger:

> An autonomous agent is about to spend money or execute a production action based on information that may be stale, hallucinated, or supplied by another agent.

Ask:

> **Who is doing what, at what moment, and what fails without us?**

If that cannot be answered concretely, the idea is not ready.

---

# 9. Buildability and dependency gate

Before committing to an idea, inspect every dependency capable of killing the demo.

## Default infrastructure when appropriate

Our normal low-friction stack is:

```text
Vercel   → frontend / web app
Railway  → APIs, workers, persistent backend processes
Supabase → Postgres, auth, storage/realtime when actually needed
GitHub   → source, CI, issues/PRs, project evidence
```

Do not add Redis, Kafka, Kubernetes, a vector database, multiple chains, five model providers, or another managed service unless the product genuinely needs it.

Prefer:

- official sponsor SDKs/testnets;
- public/free APIs;
- sponsor-provided credits;
- generous free tiers;
- deterministic local fixtures for non-core demo data;
- open datasets with usable licensing.

Material external spend must be identified **before** idea selection.

## Dependency checklist

For each critical dependency ask:

```text
Can we access it now?
Does it require approval or a waitlist?
Is there a working testnet/faucet/sandbox?
Is the SDK current and documented?
Can we run a minimal call today?
What are the rate limits / free tier / likely demo cost?
Does it require paid GPU/hardware the sponsor is not supplying?
Is the data legally and technically accessible?
Will CORS/auth/region restrictions affect the frontend?
Can it be used in the actual judging environment?
What happens if it fails during the demo?
```

For the **core sponsor capability**, fallback should not turn a fake integration into the demo. Prove the real path.

For non-core dependencies, a deterministic fallback can be valuable if it preserves the product demonstration honestly.

## Kill / pivot criteria

Strong research is allowed to kill an idea early.

Pivot if:

- the central API/hardware/network cannot be accessed or proven in time;
- the core flow requires expensive/unavailable data;
- a manual approval sits directly in the demo path;
- the idea only becomes interesting after features we cannot finish;
- the sponsor integration is decorative and there is no natural way to deepen it;
- the real-world value cannot be shown in a short end-to-end demo;
- the build requires substantially more operational surface than the deadline supports.

A killed idea is cheaper than a half-built submission.

---

# 10. Demo-first idea test

Before choosing the winner, write the demo in plain English.

A useful 60–90 second skeleton:

```text
0–10s   Show the real situation / user problem.
10–25s  Give the product a real input.
25–50s  Show the core mechanic and sponsor/platform interaction.
50–70s  Show the consequential output or user action.
70–90s  Show the result: saved time, completed transaction, recovered failure,
        generated artifact, improved experience, measurable outcome, or evidence.
```

The exact arc depends on the hackathon. A fun consumer product does not need an adversarial security demo. A verification or infrastructure product probably does.

Ask:

- What is the one screenshot or 10-second clip that explains why this product is interesting?
- Can the product produce that moment for real?
- Can the judge understand the use case without a five-minute architecture lecture?
- Does the sponsor technology visibly matter?

If the best part only exists in the roadmap, the idea is weaker than it sounds.

---

# 11. Calibrate complexity to the opportunity

There is no universal “winning architecture.” These historical references show why.

## Consumer / market-first: X Cup

The X Cup World Cup hackathon explicitly welcomed prediction markets, trading, social, NFT, GameFi, and AI-agent products, while judging differentiation, market potential, completion/demonstrability, and onchain verifiability.

The winner set was deliberately varied:

- **Billion Live — 1st:** livestream/social trading where viewers can watch and copy actions without leaving the stream;
- **ShieldSuite — 2nd:** World Cup player speculation with yield-bearing deposits and an AI trading layer;
- **WorldXI — 2nd:** onchain fantasy squad with real match-performance scoring and transparent leaderboard;
- **Choice Market — 3rd:** turns trending topics/social debates into tradeable markets;
- **CupFolio — 3rd:** AI-managed World Cup prediction portfolio;
- **Polygoal — 3rd:** World Cup outcome/exact-score prediction market with onchain settlement.

Reusable lesson:

> **When the rubric rewards traffic, engagement, creativity, and completion, a strong consumer loop can beat a technically heavier protocol. Do not mistake technical complexity for product strength.**

Reference: `https://web3.okx.com/xlayer/build-x-hackathon/xcup`

## Deep vertical workflow: Rivet

Rivet won AMD's multimodal track with a local ad-production workflow rather than a generic model demo. It used Radeon/ROCm for the actual multimodal workload, kept protected product/logo pixels outside generative authority, audited outputs before export, benchmarked the real GPU path, and made failures/reproducibility visible.

Reusable lesson:

> **When functional completeness and platform performance are central, go deep on one end-to-end workflow and make the sponsor technology visibly responsible for the result.**

References:

- `https://github.com/damishafe/Rivet`
- `https://github.com/AMD-DEV-CONTEST/Radeon-hackathon-2026-07/pull/237`

## Infrastructure can be the product: TakeGraph

TakeGraph treated generative media as a dependency graph: selective rebuilds, provider recovery, content-addressed Backblaze B2 storage, and independently re-verifiable releases. This matched a competition where production readiness, storage/data orchestration, and generative-provider integration were explicitly important.

Reusable lesson:

> **Deep infrastructure is a good bet when the sponsor and rubric are explicitly asking builders to solve pipeline, reliability, orchestration, storage, performance, or developer-infrastructure problems. It is not the default for every hackathon.**

References:

- `https://github.com/Enoch208/takegraph`
- `https://backblaze-generative-media.devpost.com/`

## Agent-economy research pattern

In agent-focused events, do not stop at “an agent that performs task X.” Research what changes when software can operate, pay, coordinate, own state, hire services, build reputation, or make decisions without a human approving every step.

Possible opportunity surfaces include:

```text
payments
budgets / credit
reputation
identity
memory
coordination
permissions
service discovery
settlement
accountability
recovery
ownership
```

Reusable lesson:

> **Ask what infrastructure, workflow, or interaction becomes necessary only when agents are genuinely autonomous. Then check whether the hackathon actually rewards that depth.**

These examples are reference points, not a menu to copy.

---

# 12. Idea slate: quality over quantity

After research, generate **about five serious concepts**, not thirty filler ideas.

Each concept must include:

```text
Name / working label
Target user
Specific real-world moment
One-sentence crux
Core mechanic
Why the sponsor/platform is naturally involved
Why this is not the generic version of the category
60–90 second demo story
Minimum complete vertical slice
Required APIs / SDKs / data / testnet / models
Likely cost
Biggest dependency/blocker
What can be faked?  → ideally nothing central; label any fixture/mock clearly
What we deliberately will NOT build
Why it could score against the actual rubric
```

At least one idea should normally be simpler than our first instinct.

At least one should explore a different user/product shape from the obvious category.

Do not force an infrastructure idea into the slate if the event clearly rewards consumer adoption, or force a consumer app if the event is a technical infrastructure challenge.

---

# 13. Rank ideas with a lightweight decision gate

Do not reuse the 100-point `goated_benchmark.md` score here. At research time most of the product does not exist yet.

Score candidate directions from 1–5 on:

| Dimension | Question |
|---|---|
| Rubric leverage | Does it attack high-value judging criteria directly? |
| Sponsor fit | Is sponsor technology naturally important to the product? |
| User clarity | Is the real-world use case immediately understandable? |
| Differentiation | Is there a specific wedge beyond a common category label? |
| Buildability | Can a solo builder complete the core in the time available? |
| Demo potency | Can the value be shown convincingly in a short real flow? |
| Dependency safety | Are APIs/data/credits/testnet/hardware realistically accessible and affordable? |

Also record:

```text
Fatal blocker? YES / NO
Complexity tax: LOW / MEDIUM / HIGH
```

Complexity is not a bonus. Every additional service, chain, model, autonomous actor, contract, queue, or external dependency should earn its existence through user value, rubric leverage, or demo value.

Use the scores to expose trade-offs, not to mechanically select the highest total.

---

# 14. P0 de-risking before serious coding

Once the top direction is selected, prove the riskiest assumptions immediately.

Examples:

- make the smallest real SDK/API call;
- deploy a tiny test contract and read it back;
- confirm faucet/credits/hardware access;
- run the required model on available hardware;
- fetch the real data source;
- perform one sponsor-native transaction;
- verify auth/CORS from the intended app environment;
- prove the hardest transformation with a fixture;
- confirm the result can be captured in the intended demo.

Do not spend two days polishing the UI before verifying the thing that can kill the project.

Once these assumptions survive, use `goated_foundation.md` to turn the direction into bounded milestones and execution.

---

# 15. Research output contract for agents

When asked:

```text
Research what we can build for <hackathon> using goated_research.md.
```

Return this structure:

```markdown
# Hackathon Research

## 1. Verified Hackathon Truth
Rules, dates, deliverables, rubric, constraints, required tech, build period.
Cite authoritative sources.

## 2. Sponsor Thesis
What the sponsor appears to want demonstrated/adopted and why.
Separate FACT from INFERENCE.

## 3. Winner + Prior-Art Archaeology
Relevant winners/comparable builds, their core mechanics, and reusable lessons.
Do not merely list projects.

## 4. Saturated / Weak Default Zones
What many teams are likely to build and what would make those categories non-generic.

## 5. Opportunity Map
Underserved users, moments, workflows, product shapes, and sponsor primitives worth combining.

## 6. Build Constraints + Dependency Reality
APIs, SDKs, data, hardware, testnets, credits, cost, approvals, and likely blockers.

## 7. Five Serious Concepts
For each: user, crux, mechanic, sponsor fit, differentiation, MVP, dependencies,
cost, demo story, explicit non-goals, and rubric fit.

## 8. Top Three Comparison
1–5 research-stage scoring + fatal blockers + complexity tax.

## 9. Recommended Direction
One primary recommendation and why it is the strongest risk-adjusted bet.
Also state what would make us abandon it.

## 10. P0 De-risking Checks
The smallest experiments to run before serious implementation.
```

Do not end with “all ideas are good.” Make a recommendation.

Do not create the full repository or architecture unless the user asked to proceed from research into building.

---

# 16. Research stopping condition

Research can become another form of procrastination.

Stop the initial research pass when we can answer:

- the official requirements and major disqualifiers;
- the sponsor thesis;
- what recent/relevant winners actually did;
- which obvious categories are crowded;
- where at least three credible opportunity directions exist;
- which direction has the best risk-adjusted combination of rubric fit, differentiation, buildability, and demo strength;
- whether its critical dependencies are accessible enough to test immediately.

Then build the smallest de-risking spike.

Return to research only when new evidence changes the decision.

---

# 17. Living research memory without bloat

This file should accumulate **research method and durable cross-hackathon signal**, not become an encyclopedia of every project we ever see.

When a new winner or postmortem is studied:

1. verify the build and result;
2. identify whether it teaches a genuinely new research lesson;
3. if yes, refine the relevant rule or add one compact reference pattern;
4. if it merely confirms an existing lesson, do not add another section;
5. put event-specific detailed research in the target project's `research/` docs rather than here;
6. if the lesson is about **how to run/build the repository**, update `goated_foundation.md` instead;
7. if the lesson is about **how to pressure-test an existing product**, update `goated_benchmark.md` instead.

Use this routing rule:

```text
What should we build? / what is the opportunity?  → goated_research.md
How should the project be organized/executed?      → goated_foundation.md
How strong is the working product?                 → goated_benchmark.md
```

> **Accumulate starting advantage, not context bloat.**

---

# Invocation examples

```text
Research what we can build for this hackathon using goated_research.md from goat_cookbook. Start from the official rules, sponsor intent, winners and ecosystem — not generic ideation. Give me five serious buildable concepts, compare the top three, and recommend the strongest one.
```

```text
Use goated_research.md to research this hackathon deeply. I am a solo builder. Prefer a complete, demoable vertical slice over a giant roadmap. Verify API/testnet/credit dependencies, avoid expensive/private APIs, and make the ideas materially different from obvious submissions.
```

```text
Run the research-stage dependency gate from goated_research.md on this idea before we build it. Tell me what can kill the project, what needs a real spike today, what the 90-second demo would look like, and whether we should continue or pivot.
```

```text
Use goated_research.md to study the latest winners from this sponsor and comparable hackathons. Extract only genuinely reusable research signal, identify crowded idea categories and negative space, then update our current idea slate. Do not modify the global research file unless a new durable principle was discovered.
```
