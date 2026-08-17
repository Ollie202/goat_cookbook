---
name: goated-foundation
description: Build and maintain an agent-ready software project foundation where the repository carries product context, current state, decisions, milestones, issues, evidence, and execution history so coding agents can work autonomously without depending on old chat context.
---

# Goated Foundation

A reusable operating skill for serious software projects.

The core principle is simple:

> **Do not make the coding agent remember the project from chat. Make the repository remember the project.**

Use this skill when starting, restructuring, or continuing a project that will be built substantially by coding agents and needs to remain understandable across many sessions, branches, milestones, integrations, and handoffs.

This skill was extracted from the project-management pattern that proved effective while building ProofRail. It is intentionally product-agnostic: copy the operating behavior, not ProofRail's architecture or domain assumptions.

## Desired outcome

A fresh coding agent should be able to enter the repository, read a small set of authoritative files, inspect the code and open work, and answer all of these without reconstructing old conversations:

- What are we building?
- Why does it exist?
- What is explicitly out of scope?
- What is actually working today?
- What is uncertain or blocked?
- What should I work on next?
- What counts as done?
- Which architectural/security decisions must I preserve?
- What real evidence proves previous milestones?
- What actions require owner approval?

If the repository cannot answer those questions, the foundation is incomplete.

---

## 1. Establish the repository as project memory

Separate stable knowledge, mutable project state, active work, history, and evidence instead of dumping everything into one giant document.

A strong default structure is:

```text
project/
├── README.md
├── AGENTS.md
├── PROJECT_STATE.md
├── CHANGELOG.md
│
├── docs/
│   ├── vision.md
│   ├── prd.md
│   ├── requirements.md
│   ├── architecture.md
│   ├── data-model.md
│   ├── api-contracts.md
│   ├── integrations.md
│   ├── security-threat-model.md
│   ├── testing-strategy.md
│   ├── deployment-runbook.md
│   ├── roadmap.md
│   └── decisions/
│       └── ADRs...
│
├── planning/
│   ├── milestones.md
│   ├── current-sprint.md
│   ├── backlog.md
│   ├── risks.md
│   └── budget.md
│
├── research/
│   ├── competitors.md
│   ├── prior-art.md
│   └── research-log.md
│
└── delivery-or-event-specific/
    ├── requirements-matrix.md
    ├── demo-plan.md
    ├── evidence.md
    └── submission-checklist.md
```

Do **not** create every file mechanically. Create only the files that carry real project information. Small projects can collapse sections. Complex or high-stakes projects should preserve the boundaries.

### File responsibilities

**README.md**  
The front door. Explain the product, problem, core workflow, status, setup, and where deeper documentation lives. It should orient a new human quickly, not contain the entire project history.

**AGENTS.md**  
The coding-agent operating contract. Define how agents must start, non-negotiable product and engineering rules, architecture boundaries, definition of done, approval boundaries, documentation discipline, cost/secrets rules, and what they must never claim or invent.

**PROJECT_STATE.md**  
The current truth. Record the present phase, what genuinely works, what does not exist yet, current blockers/unknowns, immediate objective, and any kill/rethink criteria. Update it whenever reality changes materially.

**docs/**  
Stable product and technical knowledge: what, why, how, trust/security boundaries, integrations, APIs, testing, deployment, and durable architectural explanations.

**planning/**  
Mutable execution state: milestones, current sprint, backlog, risks, and budget. These files should change as work progresses.

**docs/decisions/**  
Architecture Decision Records. Preserve *why* durable choices were made so a later agent does not "clean up" an intentional constraint.

**research/**  
Durable external learning. Record competitors, prior art, protocol/library discoveries, rejected approaches, and findings that materially affect the build.

**evidence.md or equivalent**  
Record externally verifiable proof as soon as it exists: transaction hashes, contract addresses, deployment URLs, storage roots, test results, benchmark results, integration IDs, screenshots/demo links, or other real-world evidence. Never fabricate completion evidence.

---

## 2. Make `AGENTS.md` the behavioral root

`AGENTS.md` should make a fresh agent behave like a continuation of the project rather than a new consultant with its own redesign ideas.

At minimum it should contain:

### Mission
One concise statement of what the project is trying to achieve.

### Mandatory startup routine
Before meaningful changes, require the agent to:

1. read `PROJECT_STATE.md`;
2. read `planning/current-sprint.md`;
3. read the PRD, architecture, security/trust model, and relevant integration docs;
4. read applicable ADRs;
5. inspect existing code, open issues, and current PRs before proposing rewrites.

### Non-negotiable rules
Capture project-specific truths that an agent must not reinterpret. Examples:

- do not invent security guarantees;
- do not silently broaden scope;
- do not move provider-specific code into a provider-independent core;
- do not present mocked integrations as real;
- do not expose or commit secrets;
- do not spend money, alter production, or make irreversible external changes without the defined approval gate;
- prefer a narrow working vertical slice over broad unfinished surface area.

### Definition of done
A feature or milestone is not done because code was written. Require, where applicable:

- implementation matches an explicit requirement;
- tests cover success and meaningful failure paths;
- real external integration is proven if the requirement is external;
- documentation matches implementation reality;
- evidence is recorded;
- project state/current sprint are updated;
- no stronger claim is made than the evidence supports.

This definition is what prevents agents from declaring victory after scaffolding an SDK import or producing a plausible UI.

---

## 3. Separate current truth from future intent

Never let roadmap language become mistaken for implemented reality.

Use this split:

```text
README / PRD / ROADMAP
= what the project is and where it intends to go

PROJECT_STATE
= what is objectively true right now

CURRENT_SPRINT
= what is being worked on next

ISSUES
= bounded executable units with acceptance criteria

PRs
= proposed implementation and its verification evidence
```

When an implementation lands, advance the state deliberately. Do not leave stale language saying "planned" after something works, or "complete" after a spike failed.

---

## 4. Break the build into proof-oriented milestones

Use milestones to reduce risk, not to create management theater.

Each milestone should answer one meaningful question or prove one dependency before later work relies on it.

Bad milestone:

```text
M2 — Backend
```

Better milestone:

```text
M2 — Prove external storage round trip
Outcome: canonical project evidence can be uploaded, retrieved, and verified byte-for-byte through the real provider.
```

Every milestone should have:

- **Outcome** — the real capability that will exist;
- **Acceptance criteria** — observable conditions that prove completion;
- **Dependencies** — what must already work;
- **Explicit non-goals** when scope creep is likely;
- **Evidence requirement** if external systems are involved.

Sequence milestones around technical and product risk. Prove the core mechanic before polishing the interface. Prove risky external integrations before building features that assume they work.

---

## 5. Turn milestones into GitHub Issues with acceptance contracts

Issues should not be vague TODOs. Treat each issue as an executable contract between project intent and agent implementation.

Use this pattern:

```markdown
# <Milestone / task title>

## Objective
What exact outcome are we trying to prove or deliver?

## Scope
- bounded piece of work
- bounded piece of work
- bounded piece of work

## Acceptance criteria
- [ ] observable condition
- [ ] test or failure behavior
- [ ] external evidence if required
- [ ] documentation/state updates

## Guardrails
What must not be changed, mocked, overclaimed, or spent?
```

Acceptance criteria should be difficult to game. Prefer:

- "real upload succeeds and returned bytes match" over "integrate SDK";
- "tampered input deterministically fails" over "add verification";
- "deployment transaction recorded" over "contract is deployable";
- "tests pass on clean checkout" over "tests added".

When an agent starts work, point it at a specific issue instead of saying "build the project."

---

## 6. Use a disciplined issue → branch → PR → merge loop

Default execution lifecycle:

```text
Milestone / Issue
      ↓
working branch
      ↓
implementation
      ↓
tests + failure checks
      ↓
real integration evidence where required
      ↓
docs/state updates
      ↓
draft PR
      ↓
review / CI / fix
      ↓
ready PR
      ↓
merge
      ↓
issue closes
      ↓
PROJECT_STATE + current sprint advance
      ↓
next issue
```

### Branches
Use focused branches tied to the issue or milestone. Avoid unrelated work on the same branch.

### Draft PRs
Open a draft PR when implementation is substantial enough to inspect but the acceptance criteria are not all satisfied. A draft PR is allowed to represent unfinished work honestly.

### PR description
Every substantive PR should state:

- what changed;
- why;
- how it was validated;
- what remains unproven;
- real external evidence when relevant;
- the issue it closes or references.

### Merge gate
Do not merge simply because code looks plausible. Merge when the issue acceptance criteria are genuinely satisfied and relevant CI/review checks are green.

If an external requirement is still pending, leave the PR draft or clearly incomplete.

---

## 7. Tests and evidence are the progress meter

Do not optimize for vanity test counts. Test the claims the project depends on.

For each important feature ask:

- What must succeed?
- What must fail?
- What malformed or missing input matters?
- What external failure needs structured handling?
- Which security or trust invariant must never silently degrade?

A milestone involving an external network/API/provider is **not** complete because mocks pass. Use mocks/unit tests for local behavior, but prove the real path once the milestone requires it.

Immediately record real evidence in the repository so future agents and submission/release work do not need to rediscover it.

---

## 8. Use ADRs to protect intentional decisions

Create an ADR when a choice is durable, expensive to reverse, security-sensitive, or likely to be questioned later.

Simple ADR format:

```markdown
# ADR-00X — Decision title

**Status:** Accepted
**Date:** YYYY-MM-DD

## Context
What problem or constraint forced a decision?

## Decision
What are we choosing?

## Why
Why is this better than the relevant alternatives?

## Consequences
What does this make easier, harder, required, or forbidden?
```

Do not create ADRs for trivial implementation details. Use them to preserve architectural intent.

---

## 9. Promote research into durable project knowledge

Chat research is temporary unless it changes the repository.

When research materially changes the product, architecture, trust model, integration, scope, or roadmap:

1. record the durable finding under `research/`;
2. update the affected product/technical document;
3. create or update an ADR if a durable decision changed;
4. update `PROJECT_STATE.md` if current project truth changed;
5. update issues/milestones if execution must change.

This prevents future agents from repeating already-settled research or resurrecting rejected ideas.

Distinguish:

- **fact** — verified external behavior/documentation;
- **inference** — project conclusion drawn from facts;
- **decision** — choice the project made;
- **unknown** — something not yet proven.

Never promote an unknown into a claim simply because it is convenient for the roadmap.

---

## 10. Preserve approval boundaries

Agents should continue autonomously until they reach a real owner boundary, not stop for every small decision.

Require explicit owner involvement for things such as:

- credentials or account authorization the agent cannot obtain safely;
- wallet funding or financial spend;
- production/mainnet deployment when the project defines an approval gate;
- irreversible destructive actions;
- major product decisions not resolved by existing docs;
- unavailable infrastructure requiring manual action.

When blocked, the agent should report exactly:

1. what it needs;
2. why it needs it;
3. where the owner must do it;
4. what secret/private material must **not** be pasted into chat;
5. what work can resume immediately afterward.

Do not ask the owner to manually perform tasks the connected tools can already perform.

---

## 11. Keep agents moving, not endlessly planning

A kickoff prompt should tell the implementation agent to read repository authority first, then **execute the current issue**, not return another speculative plan.

The operating rule is:

> Inspect → implement → test → debug → prove → document → PR/merge.

Planning is useful only until the next executable step is clear.

If the repository already contains an accepted plan, agents should not redesign the whole project unless new evidence invalidates it.

---

## 12. Maintain a truthful project state after every milestone

At milestone completion:

1. verify acceptance criteria;
2. merge the implementation;
3. confirm the linked issue closes or update it accurately;
4. update `PROJECT_STATE.md` with what is now genuinely true;
5. mark completed sprint items;
6. set the next objective;
7. record real evidence;
8. update relevant docs/research/ADR only where reality changed.

Do not rewrite every document after every PR. Synchronize only the files whose meaning changed.

A good `PROJECT_STATE.md` should never require reading ten PRs to understand the present situation.

---

## 13. Keep the system lean

This operating system exists to accelerate building, not create documentation work for its own sake.

Avoid:

- giant `memory.md` dumps;
- duplicate truth across many files;
- issues with no acceptance criteria;
- roadmaps pretending future features already exist;
- stale project-state files;
- PRs mixing unrelated milestones;
- fake or placeholder evidence;
- merging external integrations before proving them live;
- documentation that no agent ever reads;
- creating a database, service, token, dashboard, or abstraction simply because the structure has a place for one.

If a document does not help a future human or agent make a better decision, execute work, preserve a decision, or verify reality, it probably does not belong.

---

## 14. Recommended agent startup behavior

When this skill is applied to an existing project, the agent should do the following in order:

1. Inspect repository root, existing docs, issues, PRs, branches, tests, and recent project state.
2. Do not overwrite a mature existing structure just to match this template.
3. Identify missing **functions**, not missing filenames: agent rules, current state, architecture, active work, acceptance criteria, evidence, decision history.
4. Add or refine the minimum documents needed to close those gaps.
5. Convert the near-term build into bounded proof-oriented milestones.
6. Create or refine GitHub Issues with explicit acceptance criteria.
7. Choose the highest-priority unblocked issue.
8. Implement it on a focused branch.
9. Run meaningful tests and real integration checks.
10. Open/update a PR with validation evidence.
11. Merge only after the completion contract is satisfied.
12. Update project truth and advance to the next issue.

For a brand-new project, establish enough foundation to prevent agent drift, then begin the first technical milestone quickly. Do not spend days producing documentation before testing the riskiest assumption.

---

## 15. Quality check

The foundation is working when a new agent can enter with a prompt roughly equivalent to:

```text
Work against this repository.
Read AGENTS.md, PROJECT_STATE.md, the current sprint, relevant product/architecture/security docs, ADRs, and open issues.
Treat them as authoritative.
Continue from the highest-priority active issue.
Do not redesign settled architecture without new evidence.
Implement, test, debug, update the relevant project state/evidence, and use a focused PR.
Stop only at explicit owner/credential/spend/irreversible-action boundaries.
```

If that prompt is enough for the agent to continue coherent development without replaying old chats, the repository has become a proper project memory system.

---

# The Goated Foundation loop

```text
IDEA + RESEARCH
      ↓
VISION / PRD / ARCHITECTURE
      ↓
AGENTS.md defines how agents work
      ↓
PROJECT_STATE defines current truth
      ↓
MILESTONES reduce risk
      ↓
ISSUE defines a bounded outcome + acceptance criteria
      ↓
BRANCH
      ↓
IMPLEMENT
      ↓
TEST + REAL EVIDENCE
      ↓
PR
      ↓
REVIEW / FIX
      ↓
MERGE
      ↓
ISSUE CLOSES
      ↓
STATE + SPRINT ADVANCE
      ↓
NEXT ISSUE
```

Repeat until the product is real.
