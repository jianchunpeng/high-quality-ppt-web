---
name: high-quality-ppt-web
description: Orchestrate guizang-ppt-skill for PPT structure, humanizer-zh for Chinese copy de-AI rewriting, frontend-slides for single-file HTML slide rendering, and web-native presentation planning. Use when the user asks to generate high-quality PPT, web slides, HTML slides, front-end presentation pages, pitch decks, keynote-style decks, polished Chinese presentation documents, or needs guided help turning vague source material into a dynamic, visual, browser-based talk.
---

# High Quality PPT Web

Version: 1.6

Use this skill as a director for web-native presentation work. It coordinates:

1. `guizang-ppt-skill` for narrative structure, slide roles, and deck logic.
2. `humanizer-zh` for Chinese copy de-AI rewriting and speech-ready wording.
3. `frontend-slides` for fixed 16:9 browser slides, animation, interaction, and verification.

The skill is designed for users who may not know how to write a complete prompt. Guide them with targeted questions, propose defaults, plan visuals before generating assets, and use HTML's strengths instead of making a static PPT clone.

## Dependency Skills

Before substantial work, load these dependency skills if available:

- `C:\Users\Administrator\.codex\skills\guizang-ppt-skill\SKILL.md`
- `C:\Users\Administrator\.codex\skills\humanizer-zh\SKILL.md`
- `C:\Users\Administrator\.codex\skills\frontend-slides\SKILL.md`

If a dependency is missing, state it briefly and continue only if the request can be completed safely with this skill's references.

## Reference Map

Keep this file lean. Load reference files only when the task needs them:

- `references/intake-questions.md`: use when the brief is vague or the user needs guided prompting.
- `references/style-presets.md`: use when choosing visual direction, audience fit, or default deck style.
- `references/image-planning.md`: use before generating, placing, cropping, or embedding images.
- `references/visual-rhythm.md`: use before full-deck HTML generation, especially when a deck risks feeling repetitive or slide-to-slide layouts look too similar.
- `references/motion-patterns.md`: use when making dynamic or interactive HTML slides.
- `references/external-template-libraries.md`: use when an external HTML template library could improve visual quality, especially `zarazhangrui/beautiful-html-templates`.
- `references/template-selection-protocol.md`: use when the user should choose a visual direction from three title-slide previews.
- `references/template-adaptation-checklist.md`: use when adapting external templates, especially for Chinese typography, charts, assets, and print/PDF risks.
- `references/html-ppt-studio-integration.md`: use when `lewislulu/html-ppt-skill` can provide themes, layouts, animations, presenter mode, or PNG rendering patterns.
- `references/standard-parts-philosophy.md`: use when deciding whether to assemble from templates, charts, motion patterns, image assets, or local components instead of designing from scratch.
- `references/quality-checklist.md`: use before delivery and when diagnosing a weak deck.
- `references/slide-types.md`: use when assigning slide jobs and layouts.
- `references/design-system.md`: use as fallback visual guardrails when `frontend-slides` is unavailable or too general.
- `assets/web-slide-template/index.html`: copy or adapt when building a deck from scratch and a local template is useful.

## Core Output

Default to one browser-runnable `index.html` unless the user asks for another format.

- Fixed 1920x1080 slide stage scaled to the viewport.
- Inline CSS and JavaScript unless the project already has a build system.
- Real content, no placeholders.
- Chinese-first copy unless the user asks otherwise.
- Web-native transitions, reveal states, keyboard/click navigation, progress, and optional lightweight interactions.
- Landscape-first image assets planned before generation.
- Desktop and phone viewport checks before final delivery when browser access is possible.

If the user asks for PPTX instead of HTML, use available presentation tooling, but keep this skill's brief, image planning, copy, and quality gates as the blueprint.

## Operating Modes

Choose one mode from the user's situation:

1. Fast mode.
   - Use when the user asks to proceed directly or gives enough constraints.
   - Make expert assumptions, build, verify, and summarize assumptions.

2. Guided mode.
   - Use when the user has a topic, file, URL, or rough idea but no clear presentation brief.
   - Read/sketch the material first, then ask 3-6 targeted questions with recommended defaults.

3. Master mode.
   - Use for high-stakes, large, image-heavy, or style-sensitive decks.
   - Present a planning preview first: slide outline, visual style, image plan, motion/interaction plan, and assumptions.
   - Build only after user confirmation unless they explicitly ask you to decide.

## Workflow

1. Intake.
   - Identify audience, occasion, duration, desired outcome, tone, source material, language needs, image appetite, and interaction level.
   - If the user is vague, load `references/intake-questions.md` and ask targeted questions with your recommendation.

2. Narrative structure.
   - Load `guizang-ppt-skill`.
   - Assign every slide a job before writing final copy.
   - Use `references/slide-types.md` when selecting layouts.
   - Prefer a clear arc: hook, conflict, evidence, mechanism, implication, action.

3. Style direction.
   - Load `references/style-presets.md` when the style is not already fixed.
   - Pick one main style preset; do not mix several visual languages casually.
   - Explain the recommendation in one short sentence when asking the user to choose.

4. Template strategy.
   - If the deck needs a distinctive visual system, load `references/external-template-libraries.md`.
   - If the user has not already chosen a visual direction, load `references/template-selection-protocol.md`.
   - For `beautiful-html-templates`, match occasion and mood against `index.json`, pick three genuinely different candidates, and create title-slide previews before building the full deck.
   - For `html-ppt-skill`, use it as a structured component library: choose a theme, full-deck template, page layouts, animation pattern, and presenter-mode strategy before authoring slides.
   - If using an external template, preserve its visual system and extend missing layouts from inside that system.
   - If the user wants speed or offline work, use the local `assets/web-slide-template/index.html` instead.

5. Image plan.
   - Load `references/image-planning.md` before image generation or asset placement.
   - Do not generate AI images before the visual style is chosen or confirmed.
   - After style direction and slide jobs are known, decide per slide whether the clearest implementation is AI-generated image, SVG/process diagram, chart/map, CSS texture, typography, or no media.
   - Prefer 16:9 landscape images for a 16:9 deck.
   - Decide which slides truly need images, where each image belongs, and how crop risk will be avoided.
   - When HTML work should proceed before images are ready, reserve stable image slots with aspect ratio, crop intent, and relative asset paths, then replace them after planned assets are generated.

6. Visual rhythm plan.
   - Load `references/visual-rhythm.md` before writing the full deck.
   - Assign each slide a role, visual form, implementation choice, slot status, media treatment, and motion recipe so the deck does not become one repeated text-card pattern.
   - For long source documents, preserve complete content in appendices, detail layers, notes, or continuation slides instead of compressing every paragraph into the same main-slide layout.

7. Copy rewrite.
   - Load `humanizer-zh`.
   - Rewrite titles, bullets, transitions, and speaker notes into speech-ready Chinese.
   - Remove generic slogans, AI-like transitions, bloated abstractions, and repeated sentence shapes.

8. Planning preview.
   - In master mode, show the concise plan before implementation.
   - Include slide outline, style, image plan, visual rhythm plan, motion/interaction plan, and assumptions.
   - In fast mode, keep the plan internal and proceed.

9. HTML rendering.
   - Load `frontend-slides`.
   - Use the fixed 1920x1080 slide stage.
   - Load `references/motion-patterns.md` for dynamic or interactive decks.
   - Load `references/html-ppt-studio-integration.md` when the deck benefits from theme tokens, layout catalogs, animation catalogs, or presenter mode.
   - Load `references/standard-parts-philosophy.md` when deciding whether to use a template, chart component, image asset, motion pattern, or custom code.
   - Load `references/template-adaptation-checklist.md` before modifying an external template.
   - Adapt `assets/web-slide-template/index.html` when starting from scratch and no project scaffold exists.
   - Use small CSS/JS interactions by default; avoid heavy libraries unless requested or already present.

10. Verification.
   - Load `references/quality-checklist.md`.
   - Check desktop and phone viewport behavior when possible.
   - Verify no text overflow, incoherent overlap, broken navigation, awkward image crop, or meaningless motion.
   - Confirm every slide has a job and the deck supports a live talk.

## Non-Negotiables

- Do not generate portrait-first images for normal 16:9 slides unless the layout intentionally needs a vertical panel.
- Do not generate AI images before style direction is chosen and the slide-level media decision says an image is the right explanation tool.
- Do not fill every slide with generated art. Use images where they carry narrative or evidence.
- Do not let a long deck collapse into one repeated page pattern. Vary slide roles, density, media, diagrams, and interaction while preserving one visual system.
- Do not use generated images as decorative wallpaper only. Each generated asset needs a slide role, crop plan, and reuse/placement decision.
- Do not ask a long generic questionnaire. Ask fewer, sharper questions after reading available material.
- Do not build a static slideshow when the user asked for HTML/web slides. Add useful transitions, reveal states, navigation, and interaction.
- Do not mash layouts from different external templates into one deck. Pick one visual system and extend it consistently.
- Do not assume AI has stable visual taste. Let the user choose among real visual previews when visual direction matters.
- Do not ignore Chinese typography and chart gaps when adapting templates originally tuned for Latin text.
- Do not put presenter-only guidance on visible slides. Put scripts, cue lines, and speaking notes in hidden notes/presenter fields.
- Do not hard-code random colors when a token system exists. Use theme variables and layout primitives.
- Do not leave visual verification undone when a browser check is feasible.

## Delivery Summary

Report:

- output path
- slide count
- chosen operating mode and style preset
- guided-intake assumptions or user choices
- image plan and asset locations
- motion/interaction features
- dependency skills and references used
- verification performed
