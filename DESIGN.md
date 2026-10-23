# StudyMate design guide

Status: reference consolidation, not a new UI implementation.
Preserve [Luminous Scholar](luminous_scholar/DESIGN.md) and existing screen exports.

## Screen inventory

Every directory below contains `code.html` and `screen.png`. These are design
references, not wired routes.

| Reference | Intended purpose |
|---|---|
| [Landing](studymate_landing/code.html) | Public introduction |
| [Sign in and sign up](studymate_sign_in_sign_up/code.html) | Authentication reference |
| [Home](studymate_home/code.html) | Student overview |
| [Upload](studymate_upload_material/code.html) | Camera/PDF/paste and extracted-text review |
| [Generating](studymate_generating/code.html) | Processing state |
| [Library](studymate_library/code.html) | Saved study material |
| [Empty library](studymate_library_empty_state/code.html) | First-use state |
| [Quiz player](studymate_quiz_player/code.html) | Question/answer interaction |
| [Quiz results](studymate_quiz_results/code.html) | Score and explanations |
| [Flashcards](studymate_flashcards/code.html) | Card study |
| [Revision sheet](studymate_revision_sheet/code.html) | Summary content |
| [Weak spots](studymate_weak_spots/code.html) | Proposed topic evidence view |
| [Profile](studymate_profile/code.html) | Preferences/account |
| [Ask AI](studymate_ask_ai_rag_chat/code.html) | Future chat concept; deferred by original PRD |
| [Upload error 1](studymate_upload_error_1/code.html) / [2](studymate_upload_error_2/code.html) | Error concepts |

Home, quiz player and quiz results each have `dark_mode_1`, `dark_mode_2`,
`urdu_rtl_1` and `urdu_rtl_2` directory variants (12 additional pairs).
The upload error pair also needs a deliberate selection. Do not delete alternatives
or assume suffix 2 means approved. Teacher/class/admin screens are not present here.

## Existing visual direction

The intended tone is clear, encouraging, spacious and focused on studying.
Inter is the Latin reference font; the source guide proposes Noto Nastaliq Urdu
with larger line height for Urdu. Use semantic tokens rather than copied per-screen
styles when application components are introduced.

## Conflicts requiring resolution

| Area | Evidence | Working treatment |
|---|---|---|
| Primary color | Design front matter/Home export use #0057c2; prose says #4F8CFF | Propose token/front-matter values for implementation; confirm before restyling |
| Surface | Front matter #f9f9ff; prose #F7FAFF | Preserve exports; settle one semantic token set |
| Navigation | PRD has Home/Library/Study/Progress/Profile; guide includes Ask AI; inspected Home uses 3 tabs | Decide milestone navigation; hide unavailable destinations |
| AI quota | PRD generation limits; Home says daily AI questions | Define one unit and reset rule before displaying live quotas |
| Board coverage | Original PRD any board; exports mention Punjab/Federal/FBISE | Labels are examples, not restricted scope or endorsement |
| AI chat | Export exists; original PRD defers chat | Preserve as future reference unless scope approved |
| Confidence | Upload shows hardcoded “98% match” | Do not ship as measured OCR accuracy |
| Mastery/exam dates | Mock scores, countdowns and “high-yield” copy | Replace with measured/user-entered evidence or omit |
| Accessibility | Inspected Home disables user scaling; export text can be small | Permit zoom and test readable responsive sizing |
| Asset delivery | External Google-hosted images/fonts/icons and Tailwind CDN | Audit rights/availability; bundle approved assets for a real build |

These are documented discrepancies, not permission to rewrite product scope.

## Implementation guidelines

- One shared shell and reusable buttons, cards, forms, feedback and content components.
- Responsive mobile-first layout; desktop gets intentional width/navigation rather
  than stretching a phone composition across the full viewport.
- Use logical spacing properties for RTL. Set language/direction intentionally;
  isolate English equations, URLs and numbers inside Urdu text.
- Test Urdu shaping, diacritics, wrapping and equations together on real devices.
- Allow browser zoom, visible keyboard focus, labeled controls, screen-reader status
  announcements and sufficient contrast. Never convey correctness by color alone.
- Respect reduced motion; provide touch targets around 44px and safe-area spacing.
- Every connected screen needs loading, empty, success, permission-denied and
  recoverable-failure states as applicable.
- Source references must be reachable from questions, cards and summaries when built.
- Show a clear AI-generated/review state. Report unsupported input without fabricated
  content, timed fake success or an invented confidence score.
- Keep ads out of quizzes/assignments if later enabled. Do not infer an ad-network
  integration from the sample banner or imply a textbook-board sponsorship.
- Document light/dark token pairs and check contrast before calling dark mode ready.

## First implementation review

Once the milestone is confirmed, select canonical variants, map screens to routes,
and record a design decision. Validate upload → text review → generation → question
review → quiz → results before adding secondary screens. Inspect at narrow mobile
and desktop widths, keyboard-only, 200% zoom and supported language/theme combinations.
Current screenshot files are references, not evidence of this application's QA.
