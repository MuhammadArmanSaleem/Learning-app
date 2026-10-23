# Decision log

Record what was decided and why. This is an engineering decision history, not a
conversation transcript or private reasoning log. Preserve entries and mark replacements.
Dates use YYYY-MM-DD. Proposed entries do not imply approval or implementation.

## ADR-001 — Adopt shared project documentation

- **Date:** 2026-10-24
- **Status:** Implemented as documentation only.
- **Context:** The fork has screen exports but needs a shared product/architecture workflow.
- **Decision:** Adapt trading-agent's README, AGENTS, CLAUDE, PRD, architecture essentials,
  detailed architecture and decision-log organization; add a root DESIGN guide.
- **Rationale:** Separate requirements, technical boundaries, UI references and contributor rules.
- **Alternatives:** Copy trading-specific content verbatim; duplicate rules per agent.
- **Consequences:** Documents need maintenance and do not enforce tool compliance.
- **Evidence:** Source workflow and target repository tree inspected; application remains unbuilt.
- **Revisit when:** Documentation diverges or a tool needs a distinct entry point.

## ADR-002 — Preserve mockups and distinguish them from implementation

- **Date:** 2026-10-24
- **Status:** Implemented as documentation policy.
- **Context:** Static HTML/PNG references include hardcoded quotas, scores and processing effects.
- **Decision:** Retain all exports and original Luminous Scholar guide; document their
  purpose and conflicts in DESIGN.md.
- **Rationale:** Preserve design work without misrepresenting backend functionality.
- **Alternatives:** Delete variants or treat mock values as live product behavior.
- **Consequences:** Canonical variants/tokens still need selection before UI consolidation.
- **Evidence:** Complete tree plus design-system, Home and Upload HTML inspected.
- **Revisit when:** A connected implementation has approved canonical components.

## ADR-003 — Propose a student web vertical slice before the full platform

- **Date:** 2026-10-24
- **Status:** Proposed; scope confirmation required.
- **Context:** The original vision spans native/web, bilingual OCR, study tools and classrooms.
- **Decision:** Recommend paste/digital PDF → review text → source-linked quiz → results first.
- **Rationale:** Provides an evaluable end-to-end flow before adding delivery platforms.
- **Alternatives:** Build all screens/platforms at once; deliver only a visual prototype.
- **Consequences:** Other original requirements remain vision requirements, not deleted.
  Language order and accounts/storage choices are still open.
- **Evidence:** Existing PRD review and static exports; no implementation validation yet.
- **Revisit when:** Owner confirms milestone, team capacity and target users.

## ADR-004 — Require provenance and immutable study versions

- **Date:** 2026-10-24
- **Status:** Proposed technical contract.
- **Context:** Generated answers can be wrong, and edits can invalidate previous results.
- **Decision:** Preserve source versions/references; validate candidates and bind attempts
  and assignments to immutable question/key versions.
- **Rationale:** Makes review possible and grading history reproducible.
- **Alternatives:** Uncited content; overwrite questions in place after submissions.
- **Consequences:** Version storage and deletion/assignment retention policy must be designed.
  Schema checks do not establish factual accuracy.
- **Evidence:** Requirements analysis only; no database, worker or tests implemented.
- **Revisit when:** Implementation/evaluation or retention requirements expose a conflict.

## ADR-005 — Keep technology selection and conflicting features open

- **Date:** 2026-10-24
- **Status:** Open.
- **Context:** No app stack is installed; the original PRD lists options and designs add chat.
- **Decision:** Do not lock a backend/provider or promote mockup features into launch scope.
- **Rationale:** Avoid accidental commitments and unnecessary integrations.
- **Alternatives:** Infer a vendor from unrelated projects or implement every visible screen.
- **Consequences:** Scaffolding depends on selecting the milestone and minimum viable stack.
- **Evidence:** Repository inventory; PRD/design discrepancies recorded in DESIGN.md.
- **Revisit when:** Owner confirms platform, services, language order and feature scope.

## Template for the next decision

- **ID/title:** ADR-NNN — Concrete choice.
- **Date:** YYYY-MM-DD.
- **Status:** Proposed | Implemented | Rejected | Superseded by ADR-NNN | Open.
- **Context:** Problem, known facts and constraints.
- **Decision:** Adopted/proposed behavior.
- **Rationale:** Concise engineering justification.
- **Alternatives:** Relevant options and tradeoffs.
- **Consequences:** Benefits, costs and remaining limitations.
- **Evidence:** Actual checks, measurements or commit/PR; state if unverified.
- **Revisit when:** Conditions that justify reconsideration.

## ADR-006 — Explore PWA delivery

- **Date:** 2026-10-24
- **Status:** Proposed; expressed owner preference, not final stack approval.
- **Context:** The owner is considering establishing the app as a PWA and has not selected a stack.
- **Decision:** Evaluate an installable web application before committing to separate native clients.
- **Rationale:** Align delivery planning with the owner's stated direction.
- **Alternatives:** Ordinary responsive website; separate Android/iOS applications.
- **Consequences:** Installation targets, offline/cache behavior, updates and notifications need explicit requirements.
- **Evidence:** Owner's current instruction; no PWA implementation or device testing yet.
- **Revisit when:** The owner explains intended behavior and confirms the delivery scope.
