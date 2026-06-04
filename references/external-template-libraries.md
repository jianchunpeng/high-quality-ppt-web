# External Template Libraries

Use this when a project needs a stronger visual system than the local fallback template provides.

## Primary Library

`zarazhangrui/beautiful-html-templates`

- Repository: `https://github.com/zarazhangrui/beautiful-html-templates`
- Purpose: reusable HTML slide templates designed so coding agents can pick a suitable visual system and adapt it into a finished deck.
- License: MIT.
- Contents to read: `AGENTS.md` first, then `index.json`, then only the shortlisted template folders.

## When To Use

Use an external template library when:

- the user asks for a beautiful, polished, keynote-like, editorial, or design-forward HTML deck
- the deck's visual quality matters more than custom blank-slate coding
- the user has a clear occasion and mood but not a specific design
- the local `assets/web-slide-template/index.html` feels too generic

Avoid external templates when:

- the user needs strict offline/no-network work
- the user wants a very small one-off prototype
- the project already has a fixed design system
- the template's license or asset provenance would be inappropriate for the user's context

If cloning or downloading the external repository is required, explain the benefit and request approval when network access or external files are involved.

## Workflow For beautiful-html-templates

For candidate selection and preview details, read `references/template-selection-protocol.md`.
For modification and QA details, read `references/template-adaptation-checklist.md`.

1. Ask for occasion and mood.
   - Ask two short questions before choosing:
     - "这次演讲/汇报是什么场合？"
     - "你希望它是什么氛围：权威、克制、锋利、温暖、杂志感、科技感，还是更大胆？"
   - If the user has already given this, restate your reading and ask for correction only if uncertain.

2. Read the library operating manual.
   - Read `AGENTS.md`.
   - Read `index.json`.
   - Match by `mood`, `tone`, `best_for`, `formality`, `density`, and `scheme`.
   - Treat `occasion` as a soft signal, not a strict industry category.

3. Pick three candidates.
   - Pick three different-enough templates so the user has a real choice.
   - Include one safe fit, one expressive fit, and one wildcard if appropriate.
   - Explain each candidate by tone match, not only by industry.

4. Build title-slide previews.
   - Read each candidate's `template.html` and required sibling assets.
   - Replace the title-slide placeholders with the user's real topic, subtitle, author/date when available.
   - Save three preview HTML files in a local `previews/` folder.
   - Open or browser-check the previews when possible.
   - Ask the user which visual direction feels right.

5. Build the full deck from the chosen template.
   - Clone or copy the chosen template folder into the user's project.
   - Replace all placeholder headlines, body text, stats, names, dates, labels, and images.
   - Duplicate existing layouts when more slides are needed.
   - Remove extra slides from the bottom when fewer are needed.
   - Update page numbers and navigation state.

6. Extend missing layouts inside the chosen system.
   - Preserve fonts, palette, layout grid, decorative vocabulary, spacing rhythm, component grammar, chrome, and navigation behavior.
   - If a comparison table, timeline, map, or matrix layout is missing, design it as a natural extension of the chosen template.
   - Do not import a second template's visual language.

## Known Gaps To Plan Around

- Chart and data visualization coverage is limited; build SVG/CSS/ECharts-style additions inside the chosen template's system when needed.
- Chinese typography may need explicit fallback stacks, line-height adjustment, and title stress tests.
- Browser print or PDF export can drift when templates use absolute-positioned decorative elements; verify print/PDF separately if requested.
- The library is strongest for editorial, product, design review, founder pitch, and creative technical decks; serious academic, finance, and enterprise reporting may require more conservative adaptation.

## Candidate Selection Heuristics

- Professional but not stiff: try templates like `blue-professional`, `monochrome`, or similarly high-formality clean systems.
- Editorial and serious: look for `emerald-editorial`, `cobalt-grid`, `cartesian`, or literary/high-formality systems.
- Dramatic bilingual Chinese/English energy: consider templates that explicitly support bilingual or broadside/editorial type systems.
- Playful or workshop-like: choose lower-formality warm or pastel systems only when the audience can accept softness.
- Dense research: prefer templates with medium/high density and light schemes.
- Live keynote: prefer lower-density templates with strong title and section-slide layouts.

## Adaptation Rules

- Preserve the chosen template's fonts. Do not replace them with a familiar default just because the fallback seems close.
- Preserve the color palette and CSS variables.
- Preserve decorative elements; they are part of the identity, not optional noise.
- Preserve navigation/runtime behavior.
- Replace all placeholder content with real content.
- Keep image dimensions and frame logic unless you intentionally redesign inside the same system.
- Do not "modernize" a template that feels dated; pick a different template.

## Output Contract

When external templates are used, report:

- template library and source URL
- three preview candidates, if previews were made
- chosen template and tone rationale
- whether missing layouts were extended
- Chinese typography, chart, or PDF/export risks handled
- browser verification performed
