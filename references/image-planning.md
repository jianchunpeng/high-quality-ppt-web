# Image Planning

Use this before generating images, selecting existing visuals, or placing images in the deck.

## Principle

Plan images at the slide level before generation. The deck should not feel like images were pasted into leftover boxes.

## Timing and Slot Workflow

Generate images only after the visual style is chosen or confirmed. Before that point, discuss style, create previews, inspect source material, and draft the deck structure, but do not spend image-generation budget.

Recommended sequence:

1. Confirm the visual direction: style preset, palette, typography mood, and image appetite.
2. Build the outline and visual rhythm table: every slide has a job, density, and explanation need.
3. Decide the implementation per slide: AI-generated image, SVG/process diagram, chart/map, CSS texture, typography-only, or no media.
4. Start authoring HTML with reserved image slots when assets are not ready yet. Each slot should have a stable aspect ratio, intended crop, `data-image-slot`, and planned relative path.
5. Generate only the approved/planned AI images.
6. Replace slots with final assets and verify crop, contrast, text safety, and loading.

Image slots should preserve layout stability, for example:

```html
<figure class="media-slot media-slot--cover" data-image-slot="cover-radar" data-crop="wide, title-safe-left">
  <img src="assets/images/01-cover-abstract-radar.png" alt="" />
</figure>
```

If the asset is not generated yet, keep the slot visually calm with a CSS texture or neutral placeholder, but do not present it as final artwork.

## Image Budget

Default image budget:

- cover hero: 1 image
- section or transition visuals: 1-3 images
- key metaphor or scenario visuals: 1-3 images
- data, process, and comparison slides: usually charts, maps, diagrams, or typography instead of generated art

Do not generate one image per slide unless the deck is intentionally image-led.

For normal professional decks, a useful generated-image budget is usually 3-6 assets. These assets should be planned as reusable visual anchors: cover, section openers, mechanism backplates, or transition textures.

## Media Decision Guide

Use AI-generated images when the slide needs atmosphere, spatial context, a reusable abstract backplate, or a metaphor that cannot be drawn clearly with simple geometry.

Use SVG/process diagrams when the slide explains sequence, hierarchy, cause-and-effect, loop, risk scoring, decision rules, or relationships between known entities. Prefer diagrams over generated images when text labels and exact logic matter.

Use charts, maps, or tables when the slide depends on data, units, geographic position, comparisons, thresholds, or a verifiable evidence base.

Use CSS textures or typography-only layouts when the slide mainly needs pacing, emphasis, or a chapter transition and a generated image would only decorate the background.

## Required Image Plan Fields

For each planned image, define:

- slide number or section
- narrative role
- image type: real photo, generated image, map, chart, texture, product screenshot, diagram
- aspect ratio: default 16:9 landscape
- composition: subject position, negative space, safe crop area
- placement: full-bleed background, side panel, inline figure, chapter divider, transition asset
- crop risk: low, medium, high, plus mitigation
- storage path: deck-specific assets folder
- reuse plan: single slide, chapter family, repeated background system, or appendix/detail use

For each slide, also record the media decision even when no generated image is used:

- implementation choice: AI image, SVG/process diagram, chart/map, CSS texture, typography-only, no media
- reason: why this choice explains the content better than alternatives
- slot status: not needed, reserved, generated, inserted, verified

## Generated Image Rules

Use generated images when they add subject matter, evidence texture, atmosphere, or a reusable visual system. Do not generate images merely because the deck feels empty.

- Ask the user before generating unless they already requested image generation.
- Wait until style direction is confirmed before generating.
- For formal, public-sector, legal, safety, or infrastructure decks, prefer abstract or evidence-like visuals over fake documentary scenes.
- Generated images must contain no text, no logos, no fake UI labels, and no invented data unless the user explicitly requests those elements and they can be verified.
- If the deck uses generated abstract backgrounds, combine them with programmatic diagrams, charts, maps, or typographic layouts so the result does not feel like repeated wallpaper.
- Save generated images in a sibling `assets/images/` folder or another deck-specific assets folder, then reference them with stable relative paths.

## Landscape-First Rules

- Default to 16:9 landscape for full-slide or wide presentation images.
- Use 3:2 or 4:3 landscape for side panels.
- Use panoramic images for section transitions that pan horizontally.
- Avoid portrait images unless the layout intentionally uses a vertical portrait panel.
- Ask image generation prompts for "wide composition", "presentation background", "safe central subject", and "negative space for text" when needed.

## Placement Rules

- Full-bleed background: subject must not sit under the title; reserve 30-45% negative space.
- Side visual: keep a stable image frame; do not let text and image compete equally.
- Evidence image: use a caption explaining why the image matters.
- Transition image: match previous and next section colors so the motion feels continuous.
- Texture image: lower contrast and avoid hiding text.

## Asset Storage

Save generated or selected images in a deck-specific folder:

- `outputs/<deck-name>-assets/`
- `assets/<deck-name>/`
- a sibling `assets/` folder beside the final HTML

If the final deliverable must be a single HTML file, embed images only after confirming file size is reasonable. Otherwise, use stable relative paths.

## Prompt Skeleton

```text
16:9 landscape presentation image, [subject], [style], wide composition, safe central subject, negative space on [left/right/top] for title text, consistent lighting, no text, no logos, high detail, suitable for a professional slide deck
```

For sensitive professional decks, prefer realistic, evidence-like visuals over dramatic fantasy unless the user explicitly asks for metaphorical art.

## Abstract Report Prompt Pattern

Use this for government, safety, risk, infrastructure, and analytical report decks:

```text
16:9 landscape professional presentation background, [risk/map/process subject], deep navy and antique gold, abstract radar lines, GIS contour texture, subtle route network, wide composition, safe negative space for Chinese title text, no words, no logos, no people, no disaster photo, restrained intelligence-briefing aesthetic
```
