---
name: goated-foundation
description: Build and maintain an agent-ready software project foundation where the repository carries product context, current truth, decisions, milestones, evidence, testing, demo delivery, and execution history so agents can continue coherently without old chat context.
---

# Goated Foundation

A lean operating system for serious software projects built substantially with coding agents.

> **Do not make the agent remember the project from chat. Make the repository remember the project.**

Use this when starting, restructuring, or continuing a project across many sessions, branches, integrations, milestones, or handoffs.

Use `goated_benchmark.md` alongside it to pressure-test **product quality and competitiveness**. Keep dedicated ideation/creative-explosion material separate rather than bloating this operating layer.

---

# 1. Desired outcome

A fresh agent should be able to enter the repo and answer, without replaying old chats:

- What are we building and for whom?
- What is the sharp product thesis?
- What is explicitly out of scope?
- What genuinely works today?
- What is mocked, unknown, blocked, or unproven?
- What should be worked on next?
- What counts as done?
- Which decisions/invariants must be preserved?
- What evidence proves previous milestones?
- How is the core path tested?
- How will the product be demonstrated?
- What actions require owner approval?

If the repository cannot answer those questions, the project memory is incomplete.

---

# 2. Repository as project memory

Separate stable knowledge, current truth, active work, decisions, research, and evidence. Do not create files merely because a template lists them.

A strong default:

```text
project/
├── README.md
├── AGENTS.md
├── PROJECT_STATE.md
│
├── docs/
│   ├── prd.md
│   ├── architecture.md
│   ├── integrations.md
│   ├── security-threat-model.md
│   ├── testing-strategy.md
│   └── decisions/
│       └── ADRs...
│
├── planning/
│   ├── milestones.md
│   ├── current-sprint.md
│   └── risks.md
│
├── research/
│   └── relevant findings...
│
└── delivery-or-event-specific/
    ├── requirements-matrix.md
    ├── demo-plan.md
    ├── evidence.md
    └── submission-checklist.md
```

Collapse sections for small projects. Add files only when they carry information a future human/agent needs to decide, execute, or verify something.

## Core file responsibilities

**README.md** — front door: problem, thesis, core workflow, status, setup, proof/demo links.

**AGENTS.md** — behavioral contract: startup routine, non-negotiable rules, approval boundaries, definition of done, architecture constraints.

**PROJECT_STATE.md** — current truth only: what works, what does not, current phase, blockers, immediate objective, evidence level.

**docs/** — durable product/technical knowledge.

**planning/** — mutable execution state.

**ADRs** — why durable/expensive/security-sensitive decisions were made.

**research/** — external findings that materially influence the build.

**evidence.md** — real proof: tests, benchmark outputs, tx/storage/deployment IDs, URLs, hashes, screenshots, receipts, integration evidence. Never fabricate completion evidence.

**demo-plan.md** — exact path for showing the thesis quickly and reproducibly.

---

# 3. `AGENTS.md` is the behavioral root

A fresh agent should behave like a continuation of the project, not a new consultant redesigning it.

Require this startup routine before meaningful work:

1. read `PROJECT_STATE.md`;
2. read `planning/current-sprint.md`;
3. read PRD, architecture, security/trust and relevant integration docs;
4. read applicable ADRs;
5. inspect actual code, tests, open issues, PRs and recent commits;
6. inspect the real competition/user requirements when relevant;
7. only then decide what needs to change.

Typical non-negotiables:

- do not invent guarantees;
- do not present mocks as real integrations;
- do not silently broaden scope;
- do not redesign settled architecture without evidence;
- do not expose/commit secrets;
- do not spend money or perform irreversible external actions outside the defined approval gate;
- prefer a narrow real vertical slice over broad unfinished surface area;
- no stronger claim than the evidence supports.

---

# 4. Separate truth from intent

```text
PRD / ROADMAP
= what the project intends to become

PROJECT_STATE
= what is objectively true now

CURRENT_SPRINT
= immediate active work

ISSUES
= bounded executable outcomes

PRs
= proposed implementation + validation evidence

EVIDENCE
= what proves the claims
```

Never let roadmap language masquerade as implementation.

---

# 5. Build proof-oriented milestones

A milestone should prove one meaningful capability or retire one meaningful risk.

Bad:

```text
M2 — Backend
```

Good:

```text
M2 — Prove real storage round trip
Outcome: canonical evidence is uploaded through the real provider,
retrieved again, and verified byte-for-byte.
```

Every milestone should define:

- **Outcome** — what becomes genuinely possible;
- **Acceptance criteria** — observable proof;
- **Dependencies** — what must already work;
- **Non-goals** — where scope creep is likely;
- **Evidence level** — mock/local/external/reproducible;
- **Demo implication** — what visible moment this milestone enables, if relevant.

Sequence around risk: prove the core mechanic and risky sponsor/provider integrations before polishing secondary features.

---

# 6. Issues are acceptance contracts

Use issues as bounded contracts, not vague TODOs.

```markdown
# <Task / milestone>

## Objective
Exact outcome.

## Scope
- bounded work

## Acceptance criteria
- [ ] observable success condition
- [ ] meaningful failure condition
- [ ] real integration proof if required
- [ ] tests/evidence recorded
- [ ] demo path updated if behavior changed
- [ ] project state updated

## Guardrails
What must not be changed, mocked, overclaimed, spent, or deployed.
```

Prefer difficult-to-game criteria:

- `real upload + retrieved bytes match` over `integrate SDK`;
- `tampered input deterministically fails` over `add validation`;
- `real deployment ID recorded` over `deployable`;
- `clean-checkout test passes` over `tests added`.

---

# 7. Execution loop

```text
ISSUE
  ↓
FOCUSED BRANCH
  ↓
IMPLEMENT
  ↓
TEST HAPPY + MEANINGFUL FAILURE PATHS
  ↓
PROVE REAL INTEGRATION WHERE REQUIRED
  ↓
RECORD EVIDENCE
  ↓
UPDATE DEMO PATH IF NEEDED
  ↓
PR
  ↓
REVIEW / CI / FIX
  ↓
MERGE
  ↓
ISSUE CLOSES
  ↓
PROJECT_STATE + SPRINT ADVANCE
```

Do not merge because code looks plausible. Merge when the acceptance contract is actually satisfied.

A substantive PR should state:

- what changed;
- why;
- how it was validated;
- meaningful failure coverage;
- real external evidence when relevant;
- what remains unproven;
- linked issue.

---

# 8. Tests are claim checks

Do not optimize for vanity test counts.

For each important product claim ask:

- What must succeed?
- What must fail?
- What malformed/missing input matters?
- What provider/network failure matters?
- What stale/tampered state matters?
- Which security/trust invariant must never silently degrade?
- What must remain deterministic/reproducible?
- Does the exact demo path have coverage?

Use mocks for fast local behavior, but a milestone that claims a real external integration is not complete until the real path is proven.

Prefer a layered test strategy:

```text
unit / deterministic logic
→ integration / process boundaries
→ real local vertical slice
→ real provider/network/hardware proof
→ golden demo fixture
→ adversarial/failure fixture
```

When useful, preserve one **golden fixture** that can reproduce the canonical success path and one meaningful refusal/failure path.

---

# 9. Failure should improve the system

When a meaningful bug appears:

```text
FAILURE
→ GENERAL FAILURE CLASS
→ INVARIANT
→ TEST / GUARD / AUDIT / STATE MACHINE
→ REGRESSION PROTECTION
```

Do not merely patch the exact symptom if the failure exposes a reusable class of weakness.

Record architectural lessons in an ADR only when the decision is durable; otherwise keep the learning close to the relevant test/docs/code.

---

# 10. Evidence is the real progress meter

Track central claims using a simple ladder:

```text
E0 — idea
E1 — code/scaffolding
E2 — unit/mock proof
E3 — real local E2E
E4 — real external/provider/hardware/network proof
E5 — independently reproducible/verifiable proof
```

Do not call E2 complete when the requirement is E4.

Record evidence immediately so future agents do not have to rediscover it.

Possible evidence:

- command + raw test result;
- benchmark fixture/result;
- deployment/transaction/storage IDs;
- independently retrieved bytes/hashes;
- screenshots/video timestamps;
- provenance/receipt files;
- provider logs;
- live URLs;
- environment/device/version details.

---

# 11. Make demoability a first-class delivery concern

Do not wait until the final day to discover that the strongest engineering cannot be explained in three minutes.

For hackathons and consequential demos, maintain `demo-plan.md` or equivalent as soon as the core thesis is known.

Keep it compact:

```text
THESIS — one sentence
HOOK — problem in 10–20 seconds
INPUT — exact fixture/account/state
LIVE PATH — minimum clicks/commands proving the core mechanic
WOW MOMENT — what should stick in memory
FAILURE PATH — realistic tamper/bad model/provider failure if meaningful
PROOF — metric + receipt + sponsor evidence
CLOSE — user value + why sponsor primitive matters
```

Also record:

- exact commands/URLs needed;
- expected outputs;
- reset/setup steps;
- time budget per segment;
- fallback recording if live infrastructure dies;
- what may be cached/prerecorded and how it will be disclosed;
- final video/submission links once available.

A milestone that materially changes the canonical user flow should update the demo path while the context is fresh.

---

# 12. Build a submission-proof path, not only a product

For competition projects, aim to make the finished work easy to verify:

```text
README
  → one-sentence thesis
  → fastest setup / 60-second verification
  → live demo + video
  → benchmark/evidence links

demo-plan
  → exact judging story

evidence
  → real outputs and receipts

submission-check
  → required files
  → no secrets
  → links work
  → licenses/attribution present
  → final branch/commit known
```

The README, live app, demo video, benchmark claims, evidence, and submission text should tell the **same story**.

---

# 13. Research must become durable signal

Chat research is temporary unless it changes the repository.

When research materially changes product, architecture, scope, trust model, integration, testing, or demo strategy:

1. record the durable finding;
2. update the affected authoritative doc;
3. create/update an ADR only if a durable decision changed;
4. update `PROJECT_STATE.md` if current truth changed;
5. update issues/milestones if execution changed.

Distinguish:

- **fact** — verified external behavior;
- **inference** — conclusion drawn from facts;
- **decision** — project choice;
- **unknown** — not yet proven.

Do not promote unknowns into claims.

---

# 14. Preserve approval boundaries

Agents should keep moving until they reach a real owner boundary.

Typical owner gates:

- credentials/account authorization unavailable to the agent;
- wallet funding or financial spend;
- production/mainnet deployment when explicitly gated;
- irreversible destructive actions;
- major unresolved product decisions.

When blocked, report exactly:

1. what is needed;
2. why;
3. where the owner must do it;
4. what secret/private material must not be pasted into chat;
5. what can resume immediately afterward.

Do not ask the owner to manually do something an available tool can safely perform.

---

# 15. Keep agents executing, not replanning forever

Default behavior:

> **Inspect → implement → test → debug → prove → document → demo-check → PR/merge.**

Planning ends when the next executable step is clear.

If the repository already contains an accepted plan, do not restart ideation or redesign the architecture unless new evidence invalidates it.

---

# 16. Keep the system lean

Avoid:

- giant memory dumps;
- duplicate truth across files;
- documentation no agent reads;
- stale project-state files;
- vague issues;
- fake/placeholder evidence;
- mocks presented as real;
- PRs mixing unrelated milestones;
- speculative infrastructure;
- huge demo documents;
- copying every hackathon winner into project docs;
- creating files purely to satisfy this template.

If a file does not help a future agent **decide, execute, preserve, test, demonstrate, or verify** something, it probably does not belong.

---

# 17. Startup behavior for an existing project

1. Inspect repo root, docs, state, tests, issues, PRs, branches and recent commits.
2. Read the actual rubric/user requirements when relevant.
3. Preserve mature existing structure; identify missing **functions**, not missing filenames.
4. Find the sharpest current thesis and highest-risk unproven assumption.
5. Ensure milestones/issues have observable acceptance criteria and evidence requirements.
6. Ensure core success and meaningful failure paths are testable.
7. Ensure there is a compact demo/proof path for consequential delivery.
8. Choose the highest-priority unblocked issue.
9. Implement, test, prove, document and PR it.
10. Merge only when the acceptance contract is satisfied.
11. Update current truth and continue.

For a brand-new project, create only enough foundation to prevent agent drift, then start proving the riskiest assumption quickly.

---

# 18. Quality check

The foundation is working when a new agent can enter with something close to:

```text
Work against this repository.
Read AGENTS.md, PROJECT_STATE.md, current sprint, relevant product/architecture/security/integration docs, ADRs, tests and open issues.
Treat them as authoritative.
Continue from the highest-priority active issue.
Preserve settled architecture unless new evidence invalidates it.
Implement, test both success and meaningful failure paths, prove real integrations where required, record evidence, keep the demo path current, and use a focused PR.
Stop only at explicit credential/spend/irreversible-action/owner-decision boundaries.
```

If that is enough to continue coherent development without replaying old chats, the repository has become proper project memory.

---

# Goated Foundation loop

```text
IDEA + RESEARCH
      ↓
THESIS / PRD / ARCHITECTURE
      ↓
AGENTS.md = behavior
      ↓
PROJECT_STATE = current truth
      ↓
MILESTONE = risk/proof target
      ↓
ISSUE = acceptance contract
      ↓
IMPLEMENT
      ↓
TEST SUCCESS + FAILURE
      ↓
REAL EVIDENCE
      ↓
DEMO/PROOF PATH
      ↓
PR / REVIEW / MERGE
      ↓
STATE ADVANCES
      ↓
NEXT ISSUE
```

Repeat until the product is real, provable, and easy to demonstrate.
