# Architecture essentials

## Current repository

- Standalone HTML design exports and PNG references under `studymate_*/`.
- Original design system: [luminous_scholar/DESIGN.md](luminous_scholar/DESIGN.md).
- No connected application entry point, package manifest, API, database schema,
  authentication integration, worker, build configuration or automated tests in the
  inspected baseline.
- Exports contain external assets, sample data, placeholder navigation and some local
  interactions. They are not evidence of OCR, generation, account access or persistence.

## Proposed boundaries

- UI: upload, extracted-text review, generation status, content review, studying/results.
- Server: ownership checks, limits, validated requests and answer-key protection.
- Extraction adapter: digital text first; separate OCR support with quality evaluation.
- Generation adapter: source-grounded structured outputs, evidence references and
  validation; no secrets in browser code.
- Worker: durable bounded jobs, explicit failure/retry states and deletion checks.
- Storage: private source files, versioned text/content, attempts and quota reservations.
- External providers are replaceable adapters. Runtime, framework, auth, database,
  queue, OCR, model and hosting choices remain open.
- This is a proposed component architecture, not a claim that these modules exist.

## Product and trust constraints

- Original vision includes English/Urdu, student/teacher roles, classes and assignments,
  private uploads, quizzes, flashcards and revision sheets.
- Proposed first milestone: one responsive web student flow, pasted text/digital PDF
  to a source-linked quiz and results. It awaits scope confirmation.
- Keep evidence references mandatory in that proposed milestone; structural validation
  does not prove an answer factually correct.
- Version content before attempts. Grade on the server; do not expose assigned quiz keys.
- Prevent late workers from recreating content after deletion.
- No silent demo generation after a real provider failure.
- See [DESIGN.md](DESIGN.md): chat, quota labels, board coverage, colors and variants conflict.

Read [ARCHITECTURE.md](ARCHITECTURE.md), [PRD.md](PRD.md) and
[DECISIONS.md](DECISIONS.md). There are no verified application run/test commands yet.
