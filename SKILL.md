---
name: high-quality-ppt-web
description: Orchestrate guizang-ppt-skill for PPT structure, humanizer-zh for Chinese copy de-AI rewriting, and frontend-slides for single-file HTML slide rendering. Use when the user asks to generate high-quality PPT, web slides, HTML slides, front-end presentation pages, pitch decks, keynote-style decks, or polished Chinese presentation documents.
---

# High Quality PPT Web

Use this skill as an orchestrator. It turns a user brief into a polished web-based slide deck by chaining three specialized skills:

1. `guizang-ppt-skill` for structure, slide logic, page planning, and HTML PPT template discipline.
2. `humanizer-zh` for Chinese copy de-AI rewriting and speech-ready wording.
3. `frontend-slides` for fixed 16:9 browser rendering, animation, visual exploration, and verification.

This skill does not replace those skills. It coordinates them and adds quality gates between stages.

## Dependency Skills

Before starting substantial work, load the installed dependency skill files if they are available:

- `C:\Users\Administrator\.codex\skills\guizang-ppt-skill\SKILL.md`
- `C:\Users\Administrator\.codex\skills\humanizer-zh\SKILL.md`
- `C:\Users\Administrator\.codex\skills\frontend-slides\SKILL.md`

If a dependency is missing, say which one is missing and continue only when the request can be completed safely with the fallback rules in `references/slide-types.md` and `references/design-system.md`.

## Core Output

Default to one self-contained `index.html` unless the user asks for another format.

- Fixed 1920x1080 slide stage scaled to the viewport, following `frontend-slides`
- Inline CSS and JavaScript in the HTML file
- No external runtime dependency unless the local project already has one
- Real text content, not placeholders
- Browser-readable slides at desktop and phone viewports without reflowing the slide canvas
- Animation that supports the reading order, but no excessive motion
- Image slots or embedded images when the topic needs concrete visuals

If the user asks for PowerPoint/PPTX instead of web slides, use the presentation runtime or repo conventions available in the environment; keep this skill's structure, copy, and design rules as the content blueprint.

## Workflow

1. Intake and constraints.
   - Identify the audience, scenario, goal, constraints, tone, and decision the deck should support.
   - Ask only the few questions needed to choose structure, density, visual style, slide count, and source-material treatment.
   - If the user provides enough raw notes, continue with explicit assumptions instead of blocking.

2. Structure with `guizang-ppt-skill`.
   - Use `guizang-ppt-skill` first to shape the narrative, slide sequence, page roles, and template direction.
   - Preserve its distinction between magazine/editorial and Swiss/information-design styles when relevant.
   - Produce an outline that assigns every slide a job before writing final copy.
   - Use `references/slide-types.md` only as a local fallback or extra checklist.

3. Rewrite with `humanizer-zh`.
   - Pass titles, subtitles, bullets, speaker-style notes, and section transitions through `humanizer-zh`.
   - Remove AI-like phrasing, empty praise, generic slogans, repeated sentence forms, and long chained clauses.
   - Keep the meaning and business intent intact.
   - Make the Chinese sound like a prepared human presenter, not a report dump.

4. Render with `frontend-slides`.
   - Use `frontend-slides` for the browser implementation.
   - Follow its fixed 1920x1080 stage rule; do not reflow slide internals for mobile.
   - Include the required viewport base CSS behavior when generating a deck from scratch.
   - Use visual preview/style discovery when the user has not chosen a clear visual direction.
   - Use `references/design-system.md` only as a local fallback or quality checklist.

5. Verify before delivery.
   - Open the HTML in a browser when possible.
   - Check at least one desktop viewport and one phone viewport.
   - Confirm the 16:9 stage scales correctly.
   - Confirm text does not overflow, overlap, or become too small.
   - Confirm every slide has a clear job and no page is merely ornamental.

## Writing Rules

- Use Chinese as the primary language unless the user asks otherwise.
- Keep English terms only when they are product names, abbreviations, model names, metrics, or familiar business terms.
- Use one sharp headline per slide.
- Prefer 3-5 bullets or content blocks per slide.
- Avoid stock business jargon unless the source material requires it.
- Never leave `lorem ipsum`, `TBD`, `placeholder`, or generic sample data in the final deck.

## Frontend Rules

- Use semantic HTML sections for slides.
- Use CSS custom properties for colors, spacing, radii, and type scale.
- Use a fixed 1920x1080 slide canvas scaled as a whole to the viewport.
- Keep slide internals stable; split crowded content into more slides instead of shrinking text until it breaks.
- Prefer CSS gradients, borders, subtle shadows, and typographic contrast over heavy decoration.
- Do not use SVG-only hero art when a real or generated image would communicate the subject better.
- Keep animation optional and subtle: fade, lift, scale-in, line-reveal, or slide-right.

## Delivery

When saving output files, place the final HTML and any exported preview assets where the user can access them. Summarize:

- file path
- slide count
- selected theme or template direction
- dependency skills used
- any assumptions made from missing input
- validation performed
