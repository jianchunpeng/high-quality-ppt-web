---
name: high-quality-ppt-web
description: Orchestrate guizang-ppt-skill for PPT structure, humanizer-zh for Chinese copy de-AI rewriting, and frontend-slides for single-file HTML slide rendering. Use when the user asks to generate high-quality PPT, web slides, HTML slides, front-end presentation pages, pitch decks, keynote-style decks, or polished Chinese presentation documents.
---

# High Quality PPT Web

Version: 1.0

Use this skill as an orchestrator. It turns a user brief into a polished web-based slide deck by chaining three specialized skills:

1. `guizang-ppt-skill` for structure, slide logic, page planning, and HTML PPT template discipline.
2. `humanizer-zh` for Chinese copy de-AI rewriting and speech-ready wording.
3. `frontend-slides` for fixed 16:9 browser rendering, animation, visual exploration, and verification.

This skill does not replace those skills. It coordinates them and adds quality gates between stages.

## Version 1.0 Priorities

This skill is designed for users who may not know how to write a complete prompt. The agent must actively guide the user, infer missing decisions from the material, and offer expert defaults instead of waiting for a perfect brief.

1. Plan visuals before rendering.
   - Prefer landscape images for a 16:9 deck.
   - Avoid generating portrait images that will be heavily cropped.
   - Decide which slides truly need generated images before creating them.
   - For every planned image, define its role, aspect ratio, composition, placement, and whether it is a background, hero image, inline visual, texture, or transition asset.
   - Place images where they support the slide logic naturally; never drop images into arbitrary decorative slots.

2. Use HTML as a presentation medium, not a static PPT clone.
   - Generate dynamic and interactive web presentation material when the user asks for HTML slides or web-native decks.
   - Use page-to-page transitions, reveal sequencing, scroll or keyboard navigation, progress indicators, animated comparisons, data counters, interactive diagrams, hover/focus details, and responsive preview behavior when they improve the talk.
   - Keep motion purposeful: it should guide attention, create continuity between slides, or make a concept easier to understand.

3. Lead with guided questioning and recommendations.
   - Ask about audience, speaking scenario, desired style, duration, material source, language, visual taste, image needs, and interaction level when those choices are missing.
   - Do not ask a long generic questionnaire. Read the user's material first when available, then ask targeted questions tied to that content.
   - For each important open choice, give a recommended default and explain the tradeoff in one short sentence.
   - If the user wants speed or says to decide for them, proceed with stated assumptions.

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
- Web-native motion and interaction that support the reading order, slide transitions, and live presentation flow
- Planned image assets or embedded images when the topic needs concrete visuals, with landscape-first generation

If the user asks for PowerPoint/PPTX instead of web slides, use the presentation runtime or repo conventions available in the environment; keep this skill's structure, copy, and design rules as the content blueprint.

## Workflow

1. Intake and constraints.
   - Identify the audience, scenario, goal, constraints, tone, and decision the deck should support.
   - If source material is available, skim it before asking questions so the questions are specific.
   - Ask only the few questions needed to choose structure, density, visual style, slide count, source-material treatment, image strategy, and interaction level.
   - For users who do not know how to prompt, propose a compact recommended direction before asking them to choose.
   - If the user provides enough raw notes, continue with explicit assumptions instead of blocking.

2. Guided creative brief.
   - Convert vague asks into a usable brief with short, content-aware questions.
   - Cover, when relevant: audience, occasion, duration, presenter identity, desired outcome, tone, visual references, language mode, source fidelity, number of slides, image generation appetite, and whether interaction is wanted.
   - Ask 3-6 focused questions at a time. Include a recommended option for each open direction.
   - If the user only wants a quick result, make the choices yourself and list assumptions.

3. Structure with `guizang-ppt-skill`.
   - Use `guizang-ppt-skill` first to shape the narrative, slide sequence, page roles, and template direction.
   - Preserve its distinction between magazine/editorial and Swiss/information-design styles when relevant.
   - Produce an outline that assigns every slide a job before writing final copy.
   - Use `references/slide-types.md` only as a local fallback or extra checklist.

4. Visual and image plan.
   - Create an image plan before generating or embedding images.
   - Prefer 16:9, 3:2, or extra-wide landscape prompts for generated images.
   - State where each image belongs: full-bleed background, side visual, map layer, diagram texture, chapter divider, transition bridge, or thumbnail grid.
   - Avoid portrait-first prompts unless the slide design intentionally uses a vertical panel, character portrait, or poster crop.
   - Keep the deck visually coherent: image style, lighting, color temperature, subject distance, and texture should match the chosen theme.
   - If generated assets are saved locally, place them in a nearby `assets/`, `images/`, or deck-specific output folder and reference them with stable relative paths when possible.

5. Rewrite with `humanizer-zh`.
   - Pass titles, subtitles, bullets, speaker-style notes, and section transitions through `humanizer-zh`.
   - Remove AI-like phrasing, empty praise, generic slogans, repeated sentence forms, and long chained clauses.
   - Keep the meaning and business intent intact.
   - Make the Chinese sound like a prepared human presenter, not a report dump.

6. Present a planning preview when the direction is not already locked.
   - Before full HTML implementation, show the user a concise plan with slide outline, visual style, image plan, motion/interaction plan, and assumptions.
   - Ask for confirmation only when the work is large, image generation is involved, the style is ambiguous, or the source material could be interpreted multiple ways.
   - If the user has already asked for direct execution, keep the preview internal and proceed with stated assumptions.

7. Render with `frontend-slides`.
   - Use `frontend-slides` for the browser implementation.
   - Follow its fixed 1920x1080 stage rule; do not reflow slide internals for mobile.
   - Include the required viewport base CSS behavior when generating a deck from scratch.
   - Use visual preview/style discovery when the user has not chosen a clear visual direction.
   - Use `references/design-system.md` only as a local fallback or quality checklist.
   - Add dynamic slide transitions, reveal states, and interaction patterns that fit the live talk.
   - Use HTML/CSS/JS strengths: keyboard navigation, click targets, animated emphasis, live toggles, progressive data reveals, draggable or hoverable diagrams, and speaker-friendly progress controls.

8. Verify before delivery.
   - Open the HTML in a browser when possible.
   - Check at least one desktop viewport and one phone viewport.
   - Confirm the 16:9 stage scales correctly.
   - Confirm text does not overflow, overlap, or become too small.
   - Confirm every slide has a clear job and no page is merely ornamental.
   - Confirm generated images are not awkwardly cropped and remain meaningful at the actual slide placement.
   - Confirm transitions and interactions work by keyboard and click/tap where applicable.

## Guided Intake Pattern

When the user gives only a topic, a file, or a rough requirement, run a short consultative intake before building. The goal is not to make the user write a better prompt; the goal is to extract enough intent for the agent to design responsibly.

Ask content-aware questions such as:

- "这份材料主要讲给谁听？领导决策、客户路演、课堂分享，还是项目复盘？我建议先按目标听众来决定信息密度。"
- "你希望听众结束后做什么：理解背景、同意方案、批准预算、还是记住一个观点？我建议把这个作为主线。"
- "风格更适合哪种：杂志叙事、瑞士信息设计、科技极简、政务汇报、发布会质感？根据这份材料，我建议先选一种主风格，不混搭。"
- "需要多少现场感：静态翻页、轻量动效、还是带点击展开/数据切换/地图交互的网页演讲？我建议 HTML 版至少加入转场和分步揭示。"
- "配图要真实、抽象、生成图、还是以图表和地图为主？我建议先列出必要图片清单，再生成横版素材。"

When asking, include your recommendation. Example:

```text
我建议做成 10-12 页、科技极简 + 数据叙事风，配图只生成 4 张横版关键图，其余用地图/图表/排版完成。这样更稳，也能避免图片把专业感拉散。
```

If the user approves the recommendation or asks to proceed, build from that direction.

## Image Planning Rules

- Before image generation, produce an image plan table or short list with: slide number, narrative role, image description, aspect ratio, composition, placement, and crop risk.
- Default image prompt aspect ratio: landscape 16:9. Use "wide composition", "full-width presentation background", "safe central subject", and "negative space for title text" when a slide needs text overlay.
- For side-by-side layouts, generate 3:2 or 4:3 landscape images and reserve a stable visual frame in the slide.
- For full-bleed backgrounds, keep the main subject away from edges and leave usable negative space for typography.
- For transition images or chapter dividers, generate extra-wide or panoramic compositions if the design uses motion pans.
- Save generated images in a deck-specific folder such as `outputs/<deck-name>-assets/` or beside the HTML in `assets/`; avoid mixing unrelated deck assets.
- If the final output must be a single HTML file, embed assets only after confirming size is reasonable; otherwise keep local relative paths and tell the user where the assets are.

## Motion and Interaction Rules

- Treat the deck as a web performance: every slide should know how it enters, what reveals first, and how it exits.
- Use transitions between sections to create continuity: shared color blocks, image pan/zoom, timeline advance, map movement, line drawing, or title morph-like CSS effects.
- Use interaction for understanding, not novelty: toggles for comparison, tabs for scenarios, hover/focus labels for dense diagrams, click-to-reveal for argument steps, and animated counters for key numbers.
- Keep navigation presenter-friendly: keyboard arrows, click/tap advance, visible progress, and optional slide index.
- Respect motion comfort: no constant background motion, no fast flashing, no interaction required to read essential content.
- Prefer CSS and small JavaScript interactions in a self-contained file; only use heavier libraries when the user requests them or the project already depends on them.

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
- Use animation as an intentional part of the presentation experience: fade, lift, scale-in, line-reveal, slide-right, clip reveal, progress path, data count-up, and section transition motifs.
- Build interactive controls with accessible button semantics and clear focus states.
- Ensure images fit their containers without destructive cropping; use `object-fit: contain` when preserving the full image matters and `object-fit: cover` only when the composition was planned for it.

## Delivery

When saving output files, place the final HTML and any exported preview assets where the user can access them. Summarize:

- file path
- slide count
- selected theme or template direction
- guided-intake assumptions or user choices
- image plan and generated asset locations
- motion and interaction features included
- dependency skills used
- any assumptions made from missing input
- validation performed
