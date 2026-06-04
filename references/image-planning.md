# Image Planning

Use this before generating images, selecting existing visuals, or placing images in the deck.

## Principle

Plan images at the slide level before generation. The deck should not feel like images were pasted into leftover boxes.

## Image Budget

Default image budget:

- cover hero: 1 image
- section or transition visuals: 1-3 images
- key metaphor or scenario visuals: 1-3 images
- data, process, and comparison slides: usually charts, maps, diagrams, or typography instead of generated art

Do not generate one image per slide unless the deck is intentionally image-led.

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
