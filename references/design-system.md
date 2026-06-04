# Design System

These rules are fallback guardrails for `high-quality-ppt-web`.

When `frontend-slides` is available, its fixed 1920x1080 stage rules win over this file. Use this file for palette, typography, and quality checks, not as a replacement for `frontend-slides`.

## Structure

- Each slide is a 16:9 canvas centered in the viewport.
- Prefer a fixed 1920x1080 stage scaled uniformly to the viewport.
- Use `scroll-snap` only as a fallback when not following `frontend-slides`.
- Keep a consistent safe area: 5-7% of slide width.
- Prefer two-column, editorial grid, metric wall, process rail, comparison matrix, and split evidence layouts.
- Do not put cards inside cards.
- Keep border radius at 8px or less unless the deck is intentionally soft and consumer-facing.

## Typography

Recommended stack:

```css
font-family: "Inter", "Helvetica Neue", Arial, "Microsoft YaHei", sans-serif;
```

Use this hierarchy:

- Title: `clamp(36px, 5vw, 76px)`
- Section heading: `clamp(32px, 4vw, 56px)`
- Slide heading: `clamp(26px, 3vw, 42px)`
- Body: `clamp(15px, 1.35vw, 21px)`
- Small metadata: `clamp(12px, 1vw, 15px)`

Rules:
- Letter spacing must be `0`.
- Avoid all-caps for long English text.
- Do not scale text purely by viewport width without clamps.
- Use `line-height` from 1.12 to 1.55 depending on text size.

## Themes

Pick one theme based on subject and tone.

### classic-maestro

Use for formal, premium, board-level, strategy, consulting, and annual review decks.

- Background: `#F6F1E7`
- Text: `#1E1A16`
- Accent: `#9B1C31`
- Secondary: `#C8A25A`
- Surface: `#FFFDF8`

### deep-academic

Use for research, education, technical analysis, policy, and thought-leadership decks.

- Background: `#F4F7F8`
- Text: `#172026`
- Accent: `#1F6F8B`
- Secondary: `#2F4858`
- Surface: `#FFFFFF`

### tech-minimal

Use for AI, product, SaaS, engineering, and operational decks.

- Background: `#F7F9FC`
- Text: `#101820`
- Accent: `#2E6FDC`
- Secondary: `#16A085`
- Surface: `#FFFFFF`

### organic-natural

Use for consumer, culture, sustainability, community, and wellness topics.

- Background: `#F8F5EE`
- Text: `#1F261F`
- Accent: `#2F7D5B`
- Secondary: `#D28A39`
- Surface: `#FFFDF7`

### calm-professional

Use for internal business, HR, finance, operations, and process improvement.

- Background: `#F5F6F3`
- Text: `#202422`
- Accent: `#3A6B5B`
- Secondary: `#6C7A89`
- Surface: `#FFFFFF`

Avoid letting the full deck read as a single-hue palette. Add neutral surfaces, contrast, and one restrained accent.

## Components

- KPI blocks: large number, unit, short label, optional trend.
- Insight cards: claim, evidence, implication.
- Timeline: 3-6 milestones, consistent spacing, direct labels.
- Matrix: clear axes, highlighted cell, conclusion in the title.
- Quote: one quote only, with source and reason it matters.
- Image panel: image plus short interpretive caption, not a decorative frame.

## Animation

Use `data-anim` attributes:

- `fade-up`
- `fade-in`
- `scale-in`
- `slide-left`
- `slide-right`
- `line-reveal`

Animation should support reading order. Keep duration between 450ms and 900ms. Disable or reduce motion for `prefers-reduced-motion`.

## HTML Skeleton

```html
<main class="deck">
  <section class="slide title" data-theme="tech-minimal">
    <div class="slide-inner">
      <p class="eyebrow">...</p>
      <h1>...</h1>
      <p class="subtitle">...</p>
    </div>
  </section>
</main>
```

Use a small script to add an `is-visible` class with `IntersectionObserver` for animation triggers.
