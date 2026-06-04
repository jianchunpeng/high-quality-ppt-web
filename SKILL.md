---
name: high-quality-ppt-web
description: Create premium PPT-style web slide decks as single-file HTML presentations with Chinese-first executive copy, strong slide structure, 16:9 scroll-snap pages, responsive typography, palette systems, and lightweight animation. Use when the user asks to generate high-quality PPT, web slides, HTML slides, front-end presentation pages, pitch decks, keynote-style decks, or polished Chinese presentation documents.
---

# High Quality PPT Web

Use this skill to turn a user brief into a polished web-based slide deck: structured like a strong PPT, written like a senior Chinese presentation, and rendered as a responsive single-file HTML experience.

## Core Output

Default to one self-contained `index.html` unless the user asks for another format.

- 16:9 slide pages using `scroll-snap`
- Inline CSS and JavaScript in the HTML file
- No external runtime dependency unless the local project already has one
- Real text content, not placeholders
- Responsive layout that keeps each slide readable at desktop and mobile widths
- Animation hooks via `data-anim`, but no excessive motion
- Image slots or embedded images when the topic needs concrete visuals

If the user asks for PowerPoint/PPTX instead of web slides, use the presentation runtime or repo conventions available in the environment; keep this skill's structure, copy, and design rules as the content blueprint.

## Workflow

1. Extract the message.
   - Identify the audience, scenario, goal, constraints, tone, and decision the deck should support.
   - If the user provides messy notes, preserve the strongest facts and remove repetition.
   - If key information is missing, make conservative assumptions and keep the deck useful.

2. Build the slide logic.
   - Choose a slide count that fits the ask; default to 8-12 slides for an executive deck.
   - Use this flow: title -> context/problem -> insight/framework -> proof/data -> plan/path -> impact -> ending.
   - Use only slide types that support the message, not decorative variety.
   - For detailed slide patterns, read `references/slide-types.md`.

3. Humanize the copy.
   - Rewrite AI-like phrasing into concise, credible Chinese.
   - Prefer concrete nouns and active verbs.
   - Remove empty praise, generic slogans, repeated verbs, and long chained clauses.
   - Keep headings short; make body text sound like a prepared speaker, not a report dump.

4. Render the deck.
   - Select one of the approved visual themes, then apply it consistently.
   - Keep page structure, spacing, type scale, radius, shadows, and animation aligned with the design system.
   - For detailed visual rules, read `references/design-system.md`.

5. Verify before delivery.
   - Open the HTML in a browser when possible.
   - Check desktop and mobile widths.
   - Confirm text does not overflow, overlap, or become too small.
   - Confirm every slide has a clear job and no page is merely ornamental.

## Writing Rules

- Use Chinese as the primary language unless the user asks otherwise.
- Keep English terms only when they are product names, abbreviations, model names, metrics, or familiar business terms.
- Use one sharp headline per slide.
- Prefer 3-5 bullets or content blocks per slide.
- Avoid "赋能", "闭环", "抓手", "生态", "全链路", "底层逻辑", and similar stock phrases unless the source material requires them.
- Never leave "lorem ipsum", "TBD", "placeholder", or generic sample data in the final deck.

## Frontend Rules

- Use semantic HTML sections for slides.
- Use CSS custom properties for colors, spacing, radii, and type scale.
- Use `clamp()` for responsive sizing and spacing.
- Use stable aspect ratios and fixed layout constraints so dynamic text does not shift the design.
- Prefer CSS gradients, borders, subtle shadows, and typographic contrast over heavy decoration.
- Do not use SVG-only hero art when a real or generated image would communicate the subject better.
- Keep animation optional and subtle: fade, lift, scale-in, line-reveal, or slide-right.

## Delivery

When saving output files, place the final HTML and any exported preview assets where the user can access them. Summarize:

- file path
- slide count
- selected theme
- any assumptions made from missing input
- validation performed
