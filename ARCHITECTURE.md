# StudyMate architecture

Status: proposed architecture for implementation, 2026-10-24.
Current code consists of standalone screen exports. Paths below are responsibilities,
not existing modules. Select concrete technologies in a decision record before scaffolding.

## Existing boundaries

HTML/PNG pairs represent screens and variants. Shared styles are repeated inline,
assets often come from external URLs, and sample content is hardcoded.
There is no connected router, persistent content service or generation backend.
Preserve references while developing shared components separately.

## Proposed component model

| Component | Owns | Must not own |
|---|---|---|
| Web UI | Input, text correction, review, studying and accessible state display | Provider secrets or cross-user authorization decisions |
| Application service | Ownership, limits, jobs, content versions and submission rules | Long OCR/generation inside a fragile page request |
| Extraction adapter | File validation, text extraction/OCR and page provenance | Treating document instructions as system instructions |
| Generation adapter | Bounded provider calls and structured candidates | Arbitrary tools or trusting its own accuracy claims |
| Validation/review | Schema, references, duplication checks and review state | Claiming schema validity proves correctness |
| Worker | Job lifecycle, leases, bounded retries and completion | Recreating deleted records or charging twice |
| Persistence | Private files/text, metadata, immutable versions, attempts and usage | Public source URLs or browser-readable assigned answer keys |

Prefer one modular backend initially; the worker may run separately if runtime limits
require it. These boundaries do not require microservices or a specific vendor.

## Source to study lifecycle

1. Authorize and validate input; apply declared page/size limits and private upload policy.
2. Extract digital PDF text page by page. Route scans/images through an approved OCR
   adapter only when supported. Report extraction quality problems and allow correction.
3. Persist a text version with page/section identifiers. Chunk within provider limits
   while preserving provenance; edited pasted text uses section references.
4. Atomically reserve allowed usage and enqueue a job tied to owner, source version,
   output type/language/options and idempotency key.
5. A worker checks current authorization/deletion state, reads only relevant text and
   requests structured candidate items with exact references.
6. Validate candidates; publish only complete valid sets as reviewable AI-generated
   drafts. A source quote's existence is necessary evidence, not proof of correctness.
7. Review/edit publishes a new version. Attempts bind to a fixed quiz version.
8. Server submission checks access/answers, grades against that version and returns
   results/explanations according to the selected release policy.

Do not send a whole textbook unnecessarily. Cache within the owner's security boundary
using source version, generation settings, model/prompt version and validation version.
Cross-user reuse is a separate privacy/product decision.

## Proposed data responsibilities

| Record | Important relationships |
|---|---|
| User/profile | Owner identity, role and language; only if accounts are in the milestone |
| Upload/source | Owner, private file key, declared type/pages, deletion state |
| Text version/chunk | Source ID, version, corrected text and page/section provenance |
| Generation job | Owner/source version, options, status, attempt count, lease and idempotency key |
| Study set/item version | Owner, source evidence, format, validation/review state and immutable version |
| Quiz key | Protected answer data separated from pre-submission student payload |
| Attempt/response | User, fixed quiz version, assignment if applicable and submitted state |
| Usage reservation | User/period/job, reserved/consumed/released state |
| Class/membership/assignment | Teacher, membership state and locked published quiz version; later milestone |
| Report/audit | Target, reason and scoped sensitive-action record without unnecessary source text |

Database tables and migrations are not created by this document.
A class schema must distinguish invitation permissions, membership and source ownership.

## Job and retry rules

Proposed states: queued → extracting → generating → validating → succeeded; failures
record their failed stage. Text review may be a user step before generation is queued.
Use failed/cancelled/deleting states as appropriate. Persist checkpoints rather than
showing an invented percentage. Define which operations can safely retry.

Lease claims and completion use conditional writes/transactions. A repeated request
returns the existing job/result when its idempotency key matches. Bound retries,
execution time, pages, tokens and concurrent jobs. Release a failed reservation once
under the selected policy; publish result and consume usage atomically.
Check deletion tombstones before every expensive stage and before publication.
Provider costs can still occur on a cancelled in-flight request; report them honestly.

## Editing, attempts and assignments

Each submitted attempt references immutable questions and keys. A later edit creates
a new version rather than changing past results. Server-side idempotent submission
rejects changed answers after finalization. Client score calculations are not authoritative.
Assignment access permits reading published questions, not ownership edits or source files.
Teacher access to class results must not grant access to private self-study activity.

## Privacy and deletion

Authenticate every private request and authorize its resource relationship, including
download URLs, status polling, exports and search. Use short-lived private file links.
Uploads and model responses can contain malicious instructions/markup: isolate prompts,
limit tools and sanitize rendered output. Treat equations through a safe renderer.

Proposed deletion flow: mark source inaccessible immediately, cancel queued work,
reject late completions, delete derived private data/files and remove index/cache copies.
Specify provider retention and backup expiry before launch. The assignment/attempt
retention conflict is open; do not implement an unconditional cascade that silently
destroys classroom records. Keep logs/traces free of raw student material by default.

No provider is authorized by this plan. Verify provider data handling and required
consent before sending real private material. Use fictional evaluation fixtures.

## UI and integration contracts

The UI displays server-returned state, source references, review status, remaining
quota units/reset time and actionable errors. Do not reveal stack traces or credentials.
Keep a clear distinction between fixture demo output and real generation.
Screen names are in DESIGN.md; routing and endpoint names remain implementation decisions.

## Verification before claiming a working product

Test source parsing/provenance, insufficient input, invalid provider JSON, fabricated
references, ambiguous options, malicious source text, retries, concurrent quotas,
deletion races, immutable attempts and two-user access. Review factual quality manually.
Exercise the complete browser flow against actual services in a controlled environment;
record test commands and provider failures. No such implementation checks have run yet.

## Unselected technologies

The original PRD suggested Flutter, Next.js/Flutter Web, NestJS/Django, PostgreSQL,
Redis/jobs and private object storage as options. None is a locked repository choice.
Select the minimum stack that supports the agreed milestone; record tradeoffs in
DECISIONS.md. Do not copy trading-agent's Python/Tk architecture into this product.

## PWA direction under consideration

The owner is considering PWA delivery. Keep installability, application manifest,
service-worker lifecycle and cache policy as explicit design tasks if adopted.
PWA does not select the backend, framework or AI provider. AI generation still needs
network services unless a separate local solution is deliberately implemented.
Decide offline behavior explicitly; the original PRD specified online-only operation.
Do not cache private API responses or uploads indiscriminately. Define sign-out cache
cleanup and update behavior before permitting offline access to study material.
