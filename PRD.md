# StudyMate product requirements

Status: planning baseline, 2026-10-24. This is a repository-oriented adaptation of
the supplied StudyMate PRD v2 and existing design exports. It does not silently
approve a smaller scope or a new technology stack.

## Problem and audience

Pakistani school and college students study from textbooks, notes and syllabi in
English and Urdu. Creating useful practice from their own material takes time.
Teachers also need reusable quizzes and assignment results. These are problem
hypotheses; interviews and real sample material should validate them.

## Product vision from the supplied PRD

- Students/teachers upload PDF, images or text and generate quizzes, flashcards and
  revision sheets grounded in that material.
- Uploads are private by default. Teachers see results of their own assigned work,
  not a student's unrelated private study history.
- English and Urdu output/UI, Urdu RTL, editable extracted text and generated items.
- Classes, invitations, quiz assignments, progress tracking, quotas and administration.
- Online web, Android and iOS vision; free student access with ads as proposed funding.
- Offline use, public library, chat/forums, certificates and video are deferred in v2.
- Funding, team size, launch boards, provider choices and legal/privacy arrangements
  were not resolved by the source document.

These describe intended features, not existing repository capabilities.
The original PRD's effort/cost/timeline estimates are unvalidated planning estimates.

## Verified repository state

At inspected main commit `32015c71a563fe85829820729eca37a22a0afdc0`, the fork contains
a design-system Markdown file and 28 HTML/PNG screen pairs. No production extraction,
AI, authentication, database or deployment implementation is present. A mockup of
a feature does not establish its inclusion in the first release.

## Current delivery preference

The owner is considering an installable Progressive Web App (PWA). Treat this as the
preferred direction to explore, not a finalized framework or an offline-use commitment.
Confirm installation targets, offline behavior and notification needs before implementation.
The original native Android/iOS vision remains historical product context.

## Proposed milestones

| Stage | Outcome | Status |
|---|---|---|
| Design baseline | Preserve/export screen references and document conflicts | References exist; product decisions remain |
| Student vertical slice | Responsive web: paste/digital PDF, review text, generate quiz, review items, take quiz, results | Proposed first implementation |
| Study tools and localisation | Flashcards, revision sheets, Urdu/RTL/dark mode and OCR evaluation | Vision requirements; ordering open |
| Classroom workflow | Accounts/roles, classes, invites, immutable assignments and scoped results | Vision requirements; ordering open |
| Public launch | Quotas/admin, funding, privacy/deletion, accessibility, operational checks | Not implemented |
| Other platforms/features | Native mobile delivery and any newly approved chat feature | Open/deferred as applicable |

Do not interpret this ordering as approval to remove original requirements.
A local fixture-only prototype can precede integration, but must clearly label its
data and cannot satisfy the real generation acceptance gate.

## Proposed first-flow requirements

| ID | Requirement |
|---|---|
| P-01 | Accept pasted text or a supported digital PDF; enforce declared size/page limits before processing |
| P-02 | Preserve source pages/sections, show extracted text, allow correction and save a version |
| P-03 | Generate up to the requested 10 MCQs only from adequate source material; return fewer with a clear reason when needed |
| P-04 | Every question includes prompt, options, one declared key, explanation and evidence pointing to the source version |
| P-05 | Validate schema, unknown references, duplicate choices and missing evidence; flag semantic uncertainty for review |
| P-06 | Allow review/edit/delete/regenerate before study; edits produce new content versions |
| P-07 | Take a quiz, submit once logically, compute results against its fixed key and show explanations/references |
| P-08 | Show actual pending/running/success/failure states; bounded retry does not duplicate sets or charges |
| P-09 | Keep user content private in any shared deployment; server authorization is required before real multiuser use |
| P-10 | Delete source/derived material according to the selected policy; block late-job resurrection |

Limits, default output language, storage duration and auth/provider choices must be
set before implementing the affected integration. English-first was a recommendation
in the earlier review, not a confirmed change to the bilingual product vision.

## Acceptance gates

- A known fictional chapter yields relevant source-supported questions. A reviewer
  can follow each reference to the exact source passage.
- Too little text, an unreadable scan or unsupported file yields a clear action;
  the app does not invent a chapter or quietly return canned questions.
- Wrong-answer distractors and explanations receive human review on a benchmark;
  one marked key and valid JSON do not establish factual correctness.
- Editing a question after an attempt does not rewrite the attempt's historical key.
- Refresh/retry does not double-submit an attempt or double-create a completed set.
- Cross-user requests for source, job, content, answer key, results and file URLs fail.
- Deleting during processing cannot recreate the deleted material.
- Success/failure and real/demo modes are truthful; quota counters have a defined unit.
- Interface works with keyboard and small screens. Add mixed Urdu/English/equation
  checks before claiming Urdu support.
- Proposed small-job target remains under two minutes; measure before promising it.

A correctness threshold and benchmark size remain open. The original 90% item
correctness target should not be presented as sufficient to trust every quiz.

## Classroom rules to settle before implementation

Teachers can publish a reviewed quiz version without exposing the source file.
Students receive assigned questions without keys before submission. Teachers access
only their own class assignment results. Decide whether deleting a source also
withdraws active assignments, and what redacted historical records may be retained.
Self-study owner editing permissions must not become assigned-student edit permissions.

## Metrics

Measure successful source-to-quiz completion, time to first usable quiz, factual
correctness/ambiguity and citation support separately, repeat use, job failure rate,
cost per successful generation and deletion/authorization failures.
Weak-topic labels need enough scored evidence; minimum sample and aggregation rules
are open. Do not interpret a decorative mastery percentage as a measured metric.

## Open decisions

1. Confirm first milestone and delivery platform(s); retain the full vision separately.
2. Select runtime/framework, authentication, data store, queue, OCR/model and hosting
   based on team skills and measured requirements.
3. Confirm initial boards/subjects and language order; mockups mention Punjab/Federal
   while the source PRD says any board.
4. Chat appears in exports but is deferred in PRD v2: keep deferred unless approved.
5. Define generation units, role quotas, file limits, retry/refund and budget policies.
6. Define age/consent, provider data handling, retention and assignment deletion rules.
7. Choose screen variants, navigation and canonical design tokens; see DESIGN.md.
8. Validate demand with students/teachers and funding before any public launch.

## Traceability

- Product source: supplied “StudyMate PRD — Upload-and-Generate Study Platform”, v2.
  This Markdown is a working adaptation, not a verbatim copy of the 22-page document.
- Design source: current HTML exports and Luminous Scholar design system in this repo.
- Workflow source: trading-agent's AGENTS/CLAUDE/PRD/architecture/decision structure.
- The prior critique proposed reducing scope; no user approval of that reduction is assumed.
