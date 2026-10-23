# StudyMate Learning App

StudyMate is a proposed study platform that turns uploaded material into quizzes,
flashcards and revision sheets for Pakistani students, with English and Urdu support.

**Current state:** this repository contains standalone HTML design exports and
reference screenshots. It does not yet contain a connected study application,
authentication service, extraction pipeline, AI integration or database.
Small interactions inside an export do not establish an end-to-end feature.

## Start here

| File | Purpose |
|---|---|
| [AGENTS.md](AGENTS.md) | Shared instructions for coding agents and contributors |
| [PRD.md](PRD.md) | Product requirements, scope, acceptance criteria and open questions |
| [ARCHITECTURE-ESSENTIALS.md](ARCHITECTURE-ESSENTIALS.md) | Quick technical orientation |
| [ARCHITECTURE.md](ARCHITECTURE.md) | Proposed component boundaries, data lifecycle and security |
| [DESIGN.md](DESIGN.md) | Existing screen map, design decisions and accessibility guidance |
| [DECISIONS.md](DECISIONS.md) | Decisions, reasons, status and evidence |
| [CLAUDE.md](CLAUDE.md) | Claude entry point pointing to the shared instructions |

Read these in order before implementation. The organization follows the
[trading-agent documentation workflow](https://github.com/MuhammadArmanSaleem/trading-agent);
its trading requirements, Python desktop stack and test commands do not apply here.

## Existing design references

Each `studymate_*/` directory contains a `code.html` reference and `screen.png`.
The original design system is [Luminous Scholar](luminous_scholar/DESIGN.md).
See [DESIGN.md](DESIGN.md) for the complete screen inventory and inconsistencies.

To inspect a reference, open its `code.html` in a browser, for example
[Home](studymate_home/code.html). Fonts, icons, Tailwind and images can require
internet access. These are separate mockups, not working application routes.
Use fictional material when demonstrating them.

## Development workflow

1. Read the product and architecture docs; inspect the affected export/code.
2. Identify the milestone, acceptance criteria and any decision that blocks it.
3. Create a focused feature branch from the current target branch.
4. Implement one complete flow with explicit loading, error and empty states.
5. Verify behavior and update the relevant docs and decision records.
6. Push the feature branch and open a PR to the intended repository/base branch.
7. Report actual checks and limitations. Merge and deployment require authorization.

For this fork, the normal review target is this fork's `main`. A contribution to
`itsmhk24/Learning-app` is a separate upstream PR; do not infer that target from
GitHub's default fork comparison.

No package manager, install command, test runner or deployment command has been
selected. Add verified commands when an implementation stack is introduced.

## Planning status

The earlier StudyMate PRD describes the broad product vision. The narrower first
milestone in [PRD.md](PRD.md) is a proposal, not an approved replacement for that vision.
Provider selection, budget, launch scope and product/design conflicts remain open.

Current owner preference: explore PWA delivery. Framework/backend selection and
installation/offline requirements remain open; see ADR-006 in DECISIONS.md.
