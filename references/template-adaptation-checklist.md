# Template Adaptation Checklist

Use this before and during modification of external HTML slide templates.

## Principle

A template is not a decorative skin. It is a complete visual system: typography, spacing, palette, layout grammar, decorative vocabulary, and runtime behavior. Preserve the system, then extend it carefully.

## Before Editing

- Read the template's own instructions, if present.
- Read the template HTML and CSS variables before changing content.
- Identify the available slide layouts: cover, section, content, data, quote, comparison, ending.
- Identify navigation behavior: keyboard keys, buttons, progress, print modes.
- Identify asset dependencies: fonts, images, icons, scripts, CSS files.
- Copy the whole self-contained template folder when adapting, not a single HTML file if sibling assets exist.

## Content Replacement

Replace all placeholders:

- title and subtitle
- author, team, date, version
- section titles
- body copy
- stats and units
- chart labels
- image captions
- names, roles, company names
- URLs and QR placeholders
- page numbers or navigation labels

Never leave generic demo language in the final deck.

## Chinese Typography

Many beautiful HTML templates are tuned for Latin text. Add Chinese safeguards:

- Provide a Chinese fallback stack such as `"Noto Sans SC", "Source Han Sans SC", "Microsoft YaHei", sans-serif`.
- Test long Chinese titles in the actual template layout.
- Avoid letter spacing on Chinese text unless the template explicitly handles it well.
- Check whether serif display fonts make Chinese look broken or inconsistent.
- Adjust line-height and max-width for Chinese paragraphs; Chinese often needs different rhythm than English.
- Preserve the template's Latin display font for English if it is part of the identity.

## Charts and Data

Many external templates lack chart components. When adding data visuals:

- Build charts inside the chosen template's palette and spacing system.
- Prefer inline SVG, CSS charts, or lightweight canvas when the deck is self-contained.
- Use ECharts or another library only if allowed by the project and network/offline constraints.
- Add direct labels, units, and a takeaway.
- Match axis, grid, stroke, fill, and annotation style to the template.
- Do not paste a chart style from another template.

## Images and Assets

- Keep the template's image frame logic unless intentionally extending it.
- Replace generic stock placeholders with real or planned visuals.
- Use landscape-first assets for 16:9 decks.
- Keep important subjects away from cropped edges.
- Check asset paths after copying folders.
- Do not hotlink remote images unless the user accepts network dependence.

## Layout Extension

If the source material needs a layout not present in the template:

- Derive it from existing grid, spacing, type scale, surfaces, borders, and decorative motifs.
- Reuse existing components before inventing new ones.
- Create one new layout role at a time: matrix, timeline, map, chart, process, appendix.
- Keep navigation and progress behavior consistent.
- Avoid importing CSS, components, or visual motifs from another template.

## Print and PDF Risk

Browser decks may not print cleanly by default.

Before claiming PDF readiness:

- Test browser print preview or PDF export when possible.
- Watch absolute-positioned decorative elements.
- Check page breaks, clipping, fixed backgrounds, and oversized transforms.
- Add print CSS only if export matters.
- If PDF export is not verified, say so plainly.

## Browser QA

Check:

- desktop viewport
- phone viewport with 16:9 scaling
- title slide
- densest text slide
- chart/data slide
- image-heavy slide
- final slide
- console errors
- keyboard navigation
- reduced motion if meaningful
