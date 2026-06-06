# Quality Checklist

Use this before delivery and when diagnosing a weak deck.

## Brief

- Audience is clear.
- Desired outcome is clear.
- Duration or slide count is appropriate.
- One style preset dominates the visual direction.
- Assumptions are stated when the user did not decide.
- If visual direction matters, the user chose from real previews or the skipped-preview assumption is stated.

## Structure

- Every slide has a job.
- The title of each slide contains the point, not just the topic.
- The deck has a visible arc: hook, conflict, evidence, mechanism, implication, action.
- No slide is only ornamental unless it is a deliberate section transition.
- Crowded slides are split instead of shrinking text until it breaks.

## Copy

- Chinese sounds like a prepared presenter, not a report dump.
- No `lorem ipsum`, `TBD`, placeholders, or generic sample data.
- Bullets are short and parallel enough to scan.
- Important numbers have units, ranges, and interpretation.
- English is kept only when useful: product names, metrics, abbreviations, or bilingual requirement.

## Visuals

- Image plan exists before generated images are used.
- No AI image was generated before the visual direction was chosen or confirmed.
- The outline/rhythm plan marks each slide's implementation choice: AI image, SVG/process diagram, chart/map, CSS texture, typography-only, or no media.
- SVG/process diagrams are used where they explain exact sequence, logic, scoring, or relationships more clearly than generated images.
- HTML image slots are stable before asset insertion: fixed aspect ratio, intended crop, `data-image-slot` or equivalent identifier, and relative path.
- Normal slide images are landscape-first.
- No important subject is cropped off.
- Images support the argument instead of filling space.
- Charts and maps have direct labels, units, and takeaways.
- The palette is not a single-hue wash.
- If an external template is used, one visual system is preserved instead of mixing templates.
- Template placeholders, stats, dates, names, labels, and image slots are all replaced with real content.
- Chinese typography has been checked in the actual layout, especially title slides and dense body slides.
- Added charts or data components match the chosen template's palette, spacing, and component grammar.
- Theme colors, type scale, surfaces, and accents come from a token system or coherent template variables.
- Layouts are selected as reusable page roles instead of improvised one-off pages.
- Screenshot thumbnails show rhythm: section openers, content slides, diagrams, detail layers, and synthesis pages are visually distinguishable.
- No three consecutive main slides use the same layout, density, and motion recipe unless it is a deliberate repeated sequence.
- Generated images have a visible purpose and do not function as repeated wallpaper behind every slide.

## Motion and Interaction

- Keyboard and click/tap navigation work.
- Progress is visible.
- Reveal order matches speaking order.
- Section transitions feel consistent.
- Interaction helps comparison, explanation, or pacing.
- Reduced-motion behavior exists or motion is restrained enough to be acceptable.
- Presenter-only notes, scripts, and cue lines are hidden from audience slides.
- Presenter mode, overview mode, or speaker notes are checked if included.
- Animations are purposeful and not stacked into visual noise.

## Browser Verification

- Desktop viewport checked.
- Phone viewport checked with the 16:9 stage scaling intact.
- No text overflow or incoherent overlap.
- Buttons and interactive controls have focus states.
- Browser console has no blocking errors.
- Referenced local assets load correctly.
- If template previews were created, each preview was opened or browser-checked before asking the user to choose.
- PNG/PDF/export output is separately verified if the user requested export-ready files.

## Failure Signals

Revise if any of these appear:

- the user had to write a full prompt to make the skill useful
- every slide has a generated image without a reason
- the HTML deck feels like exported static PPT
- images are portrait-cropped into 16:9 frames
- the deck looks stylish but does not support a live talk
- the deck mixes multiple template languages
- Chinese text looks weaker than the Latin typography
- charts look pasted in from a different design system
- presenter notes leak onto audience-visible slides
- theme tokens are ignored and random hard-coded colors accumulate
- the final answer says "not verified" when verification was feasible
- the deck feels monotonous because every page uses the same title/list/card formula
