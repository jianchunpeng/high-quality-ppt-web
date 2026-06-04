# html-ppt-skill Integration

Use this when learning from or optionally using `lewislulu/html-ppt-skill`.

## Source

- Repository: `https://github.com/lewislulu/html-ppt-skill`
- Purpose: static HTML presentation studio with theme tokens, layout files, full-deck templates, animations, runtime navigation, presenter mode, speaker notes, and render scripts.
- License: MIT.
- Do not install or clone it automatically unless the user approves network access and external files. You can still learn from its method and route future work toward it.

## What To Reuse Conceptually

This project is valuable because it treats presentation authoring as composable standard parts:

- one theme file equals one visual look
- one layout file equals one page type
- one animation class or data attribute equals one entry effect
- one runtime provides keyboard navigation, overview, notes, presenter mode, and preview behavior
- one render script creates PNG screenshots for verification

This matches `high-quality-ppt-web`'s standard-parts philosophy. Prefer assembling from proven parts before inventing from a blank page.

## When To Consider It

Consider `html-ppt-skill` when:

- the user needs a professional HTML slide deck with many layout types
- the deck needs charts, code, diagrams, timelines, roadmaps, gantt, architecture, or process slides
- the user mentions 演讲, 分享, 讲稿, 逐字稿, speaker notes, presenter view, or 提词器
- the user needs theme switching, keyboard navigation, overview grid, fullscreen, or export screenshots
- the deck should support Chinese and English cleanly

Prefer `beautiful-html-templates` when the main need is high-end visual direction chosen from designer-like template previews.
Prefer `html-ppt-skill` when the main need is a production-ready slide system with many reusable parts and presenter workflow.

## Intake Additions

Before authoring, clarify or infer:

- audience: engineers, executives, consumers, students, VC, design/product team
- length: 5-minute lightning talk, 20-minute share, 45-minute session, 1-hour training
- language: Chinese, English, bilingual
- format: live screen talk, PDF/PNG export, 小红书图文, internal report
- tone: clinical, playful, editorial, cyber, academic, corporate, launch-like
- presenter support: none, notes only, full presenter mode with script and timer

If the user is unsure, recommend 2-3 theme directions and one full-deck starting point.

## Theme Strategy

Use token-driven themes instead of hard-coded colors.

Map common cases:

- business or investor pitch: `pitch-deck-vc`, `corporate-clean`, `swiss-grid`
- technical sharing or engineering: `tokyo-night`, `dracula`, `catppuccin-mocha`, `terminal-green`, `blueprint`
- 小红书 or consumer-facing: `xiaohongshu-white`, `soft-pastel`, `rainbow-gradient`, `magazine-bold`
- academic or report: `academic-paper`, `editorial-serif`, `minimal-white`
- edgy launch or cyber: `cyberpunk-neon`, `vaporwave`, `y2k-chrome`, `neo-brutalism`

If implementing a compatible deck, provide theme alternatives when possible so users can audition them visually.

## Layout Strategy

Do not hand-author each page from scratch. Pick page roles first, then map each role to a layout type.

Useful layout families:

- openers: cover, toc, section-divider
- text: bullets, two-column, three-column, big-quote
- numbers and data: stat-highlight, kpi-grid, table, chart-bar, chart-line, chart-pie, chart-radar
- code and terminal: code, diff, terminal
- diagrams: flow-diagram, arch-diagram, process-steps, mindmap
- planning and comparison: timeline, roadmap, gantt, comparison, pros-cons, todo-checklist
- visuals: image-hero, image-grid
- closers: cta, thanks

Avoid repeating the same layout twice in a row unless the repetition is intentional.

## Animation Strategy

Use animations as controlled accents.

- Cover/title: `rise-in` or `blur-in`
- Body content: `fade-up`
- Grids/lists: `stagger-list`
- Stats: `counter-up`
- Diagrams: `path-draw`
- Section dividers: restrained 3D or perspective effects only when the style allows
- Closers: celebratory effects only when appropriate

Use at most one accent animation per slide plus a calm supporting reveal. Avoid stacking many effects.

Canvas FX are powerful but should be rare. Use one FX per slide at most, and only when it fits the audience.

## Presenter Mode and Speaker Notes

If the user is giving a live talk, add presenter support.

Use these rules:

- Put presenter-only material in hidden notes or presenter fields, never on visible slides.
- Speaker notes are cue signals, not prose to read word-for-word.
- For full scripts, target 150-300 Chinese words per slide.
- Bold core keywords.
- Put transition sentences in separate short paragraphs.
- Write in spoken Chinese: "所以", "但是", "接下来", not stiff report language.
- End each note with a natural bridge to the next slide.

When using a runtime with presenter mode, support:

- current slide preview
- next slide preview
- speaker script
- timer
- keyboard navigation
- synchronization between presenter and audience windows

## Verification Pattern

Borrow this verification mindset:

- browser-walk every slide with keyboard navigation
- open overview/grid mode when available to catch clipping
- test theme switching if the deck supports alternate themes
- open presenter mode if notes/scripts are included
- render PNG screenshots when feasible
- verify the densest slide, chart slide, image slide, and final slide

If PNG/PDF export is requested, verify export separately. Do not assume browser-live layout and print/export layout are identical.

## What Not To Copy Blindly

- Do not add heavy external runtimes if the current deck can stay self-contained.
- Do not force theme cycling into a formal deliverable if it distracts from the user goal.
- Do not use dramatic FX for government, boardroom, academic, or safety-critical decks.
- Do not clone or install the external skill without user approval.
- Do not overwrite this skill's guided-intake and template-preview workflow; use `html-ppt-skill` as an optional source of parts and implementation patterns.
