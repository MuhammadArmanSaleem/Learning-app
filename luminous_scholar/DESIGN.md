---
name: Luminous Scholar
colors:
  surface: '#f9f9ff'
  surface-dim: '#cfdaf2'
  surface-bright: '#f9f9ff'
  surface-container-lowest: '#ffffff'
  surface-container-low: '#f0f3ff'
  surface-container: '#e7eeff'
  surface-container-high: '#dee8ff'
  surface-container-highest: '#d8e3fb'
  on-surface: '#111c2d'
  on-surface-variant: '#424753'
  inverse-surface: '#263143'
  inverse-on-surface: '#ecf1ff'
  outline: '#727785'
  outline-variant: '#c2c6d6'
  surface-tint: '#0059c6'
  primary: '#0057c2'
  on-primary: '#ffffff'
  primary-container: '#2c70e2'
  on-primary-container: '#fefcff'
  inverse-primary: '#afc6ff'
  secondary: '#006c4b'
  on-secondary: '#ffffff'
  secondary-container: '#64f9bc'
  on-secondary-container: '#00714e'
  tertiary: '#765700'
  on-tertiary: '#ffffff'
  tertiary-container: '#956e00'
  on-tertiary-container: '#fffbff'
  error: '#ba1a1a'
  on-error: '#ffffff'
  error-container: '#ffdad6'
  on-error-container: '#93000a'
  primary-fixed: '#d9e2ff'
  primary-fixed-dim: '#afc6ff'
  on-primary-fixed: '#001a43'
  on-primary-fixed-variant: '#004398'
  secondary-fixed: '#68fcbf'
  secondary-fixed-dim: '#45dfa4'
  on-secondary-fixed: '#002114'
  on-secondary-fixed-variant: '#005137'
  tertiary-fixed: '#ffdf9f'
  tertiary-fixed-dim: '#f9bd22'
  on-tertiary-fixed: '#261a00'
  on-tertiary-fixed-variant: '#5c4300'
  background: '#f9f9ff'
  on-background: '#111c2d'
  surface-variant: '#d8e3fb'
typography:
  headline-lg:
    fontFamily: Inter
    fontSize: 32px
    fontWeight: '700'
    lineHeight: 40px
    letterSpacing: -0.02em
  headline-lg-mobile:
    fontFamily: Inter
    fontSize: 26px
    fontWeight: '700'
    lineHeight: 34px
    letterSpacing: -0.02em
  headline-md:
    fontFamily: Inter
    fontSize: 24px
    fontWeight: '600'
    lineHeight: 32px
    letterSpacing: -0.015em
  headline-sm:
    fontFamily: Inter
    fontSize: 20px
    fontWeight: '600'
    lineHeight: 28px
    letterSpacing: -0.01em
  title-lg:
    fontFamily: Inter
    fontSize: 18px
    fontWeight: '600'
    lineHeight: 26px
  title-md:
    fontFamily: Inter
    fontSize: 16px
    fontWeight: '600'
    lineHeight: 24px
  body-lg:
    fontFamily: Inter
    fontSize: 16px
    fontWeight: '400'
    lineHeight: 26px
  body-md:
    fontFamily: Inter
    fontSize: 14px
    fontWeight: '400'
    lineHeight: 22px
  body-sm:
    fontFamily: Inter
    fontSize: 12px
    fontWeight: '400'
    lineHeight: 18px
  label-lg:
    fontFamily: Inter
    fontSize: 14px
    fontWeight: '600'
    lineHeight: 20px
    letterSpacing: 0.01em
  label-md:
    fontFamily: Inter
    fontSize: 12px
    fontWeight: '500'
    lineHeight: 16px
    letterSpacing: 0.02em
  label-sm:
    fontFamily: Inter
    fontSize: 11px
    fontWeight: '500'
    lineHeight: 14px
    letterSpacing: 0.03em
rounded:
  sm: 0.25rem
  DEFAULT: 0.5rem
  md: 0.75rem
  lg: 1rem
  xl: 1.5rem
  full: 9999px
spacing:
  gutter: 1rem
  margin: 1.25rem
  space-xs: 0.25rem
  space-sm: 0.5rem
  space-md: 1rem
  space-lg: 1.5rem
  space-xl: 2rem
---

## Brand & Style
This design system crafts an encouraging, clear, and reassuring atmosphere tailored for secondary and higher secondary students navigating rigorous curricula (Matriculation, FSc, and Cambridge O/A-Levels). The emotional objective is to dissolve academic anxiety and substitute it with structured clarity, approachable intelligence, and sustained motivation.

The visual direction embraces **Soft Modern Minimalism**:
- **Light & Airy:** Generous breathing room with deliberate padding, preventing cognitive overload during dense exam preparation sessions.
- **Friendly & Approachable:** Gentle radii, clear visual scaffolding, and buoyant sky tones that bridge casual peer-to-peer collaboration with focused self-study.
- **Bilingual Sensibility:** Tailored to harmonize English typography with the natural vertical cadence and baseline demands of Nastaliq/Urdu scripts.
- **Supportive Clarity:** State feedbacks (success, alert, error) are clear, uplifting, and non-punitive, celebrating incremental study milestones.

## Colors
The color palette uses a bright sky-blue anchor with deliberate tint layers to establish a calm, distraction-free environment:

- **Primary (`#4F8CFF`):** Bright Sky Blue. Used for core interactive cues, primary calls-to-action, bottom navigation active indicators, and prominent progress highlights.
- **Primary Tint / Soft Ground (`#EAF3FF`):** Used for selection pills, active card states, conversational AI message bubbles, and icon backing fills.
- **Secondary / Mint (`#34D399`):** Represents success, mastery badges, correct answers in practice sets, and finished goal markers.
- **Tertiary / Amber (`#FBBF24`):** Designates active study streaks, daily query quotas, pacing warnings, and revision deadlines.
- **Accent Coral (`#F87171`):** Applied strictly to incorrect solutions, overdue notices, and system alerts.
- **Canvas Base (`#F7FAFF`):** An airy off-white with cool undertones that minimizes eye fatigue during late-night revision sessions.
- **Surface Elevation (`#FFFFFF`):** High-clarity white for cards, bottom sheet dialogs, and persistent bars.
- **Neutral Primary (`#1E293B`):** Deep slate providing crisp legibility for body, titles, and mathematical notation.
- **Neutral Muted (`#64748B`):** Balanced slate for metadata, secondary timestamps, subtitles, and disabled states.

## Typography
The typographic system relies on **Inter** for its neutral readability, balance at dense informational scales, and clear distinction between glyphs (crucial for formulas and structured notes).

### Multilingual Support (Urdu Nastaliq)
When rendering Urdu content (such as Islamiat, Urdu literature, or localized Pakistan Studies prompts):
- The system cascades cleanly to `Noto Nastaliq Urdu` or system Nastaliq fonts.
- Nastaliq requires a minimum line-height multiplier of `1.8x` to `2.2x` and a font size step approximately `2px` larger than corresponding Latin tokens to balance visual weight and avoid diacritic clipping.
- Alignments mirror gracefully in RTL viewports with right-aligned anchors.

## Layout & Spacing
The layout model is anchored on a 4px/8px incremental rhythm configured for high-density touch targets and airy visual hierarchy:

- **Mobile Viewports (<640px):** Single-column fluid view with `1.25rem` (20px) outer edge margins to maintain touch security. Component stacks use `space-md` (16px) vertical gutters.
- **Tablet / Large Handheld (640px - 1024px):** 6-column fluid structure with `1.5rem` (24px) gutters, shifting multi-step problem solving, flashcard desks, or dual split-screen study modes side-by-side.
- **Safe Area Insets:** Persistent bottom navigation maintains automatic safe padding at device bottoms (`env(safe-area-inset-bottom) + 0.5rem`).

## Elevation & Depth
Depth is produced through subtle surface tonal contrast combined with soft, light-diffused ambient drops:

- **Base Layer (Flat):** Surface tone `#F7FAFF` handles background scaffolding.
- **Card Tier (Resting):** Pure white (`#FFFFFF`) containers resting on `#F7FAFF` featuring an ambient shadow: `box-shadow: 0 4px 20px -2px rgba(79, 140, 255, 0.07), 0 2px 6px -1px rgba(30, 41, 59, 0.04);`.
- **Floating / Elevated Panels (Bottom Sheets, Snackbars):** Elevated cards incorporate deeper diffusion: `box-shadow: 0 12px 32px -4px rgba(79, 140, 255, 0.12), 0 4px 12px -2px rgba(30, 41, 59, 0.06);`.
- **Borders & Dividers:** Outlines avoid harsh grays, using an ultra-faint tone `rgba(79, 140, 255, 0.12)` or `rgba(100, 116, 139, 0.08)` to sustain softness.

## Shapes
The shape language uses balanced curvature (`roundedness: 2`) to maintain a friendly, approachable, yet well-ordered study workspace:

- **Cards & Content Surfaces:** Standardized at `1rem` (16px, `rounded-lg`) corner radii to soften visual boundaries.
- **Form Controls & Action Buttons:** Radii calibrated to `0.75rem` - `1rem` for effortless finger placement.
- **Category Tags, Badges & Floating Pills:** Fully curved pill shapes (`9999px` / `rounded-full`) to differentiate interactive chips from structural containers.

## Components

### Buttons
- **Primary Button:** `#4F8CFF` fill, `#FFFFFF` text, `12px` vertical padding, `20px` horizontal padding, `12px` border-radius (`rounded-lg`), bold label. Active press yields subtle `scale(0.98)` feedback with gentle brightness reduction.
- **Secondary Button:** `#EAF3FF` surface, `#4F8CFF` text, no border.
- **Outline / Ghost:** Transparent fill with `1px` border of `rgba(79, 140, 255, 0.3)` and `#4F8CFF` label.

### Cards
- Pure `#FFFFFF` background, `16px` border-radius, soft ambient drop shadow, `16px` or `20px` internal padding.
- **Interactive Subject Cards:** Display course badge (e.g., "O-Level Physics"), progress indicator in secondary mint, and chapter count in `#64748B`.

### Bottom Navigation Bar (5 Tabs)
- Fixed at screen base: Home, Library, Ask AI, Progress, Profile.
- Pure `#FFFFFF` fill with an ultra-soft top separator: `1px solid rgba(79, 140, 255, 0.08)`.
- Icon paired directly with `label-sm` text.
- **Active State:** Tab icon and label illuminate in `#4F8CFF`. The center action ("Ask AI") is emphasized with an elevated `#4F8CFF` circle, white icon, and glowing ambient blue halo.
- **Inactive State:** Tinted `#64748B` with `18px` icon footprint.

### Input Fields & Chat Prompt Box
- Inputs use `#FFFFFF` background with `1px solid rgba(100, 116, 139, 0.2)` border, expanding to `2px solid #4F8CFF` on focus with `#EAF3FF` subtle outer focus ring.
- **Ask AI Input Bar:** Sticky input container with camera/upload action for past-paper questions, voice mic action, and sky-blue send pill.

### Chips & Filter Pills
- `rounded-full` height `32px` to `36px`, filled with `#FFFFFF` or `#EAF3FF`, with `#1E293B` text. Active filters snap to `#4F8CFF` with white text.

### Progress Trackers & Quota Meters
- Soft track (`#EAF3FF`) paired with animated `#4F8CFF` fill for study pacing, or `#FBBF24` for remaining daily AI token queries.