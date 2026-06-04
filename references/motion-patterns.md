# Motion and Interaction Patterns

Use this when building HTML slides that should feel dynamic or interactive.

## Principle

Motion should guide attention, explain sequence, or connect sections. Interaction should improve understanding, not decorate the deck.

## Baseline Controls

Every web deck should support:

- keyboard arrows
- click or tap advance
- visible progress
- current slide state
- reduced-motion fallback

## Slide-Level Motion

- title reveal: eyebrow, title, subtitle, metadata
- evidence reveal: claim first, then data, then implication
- comparison reveal: show baseline, show contrast, then highlight decision
- diagram reveal: draw path or reveal nodes in order
- image reveal: slow crop/clip reveal or subtle pan only when it supports the story

## Section Transitions

Use one transition motif per deck:

- color band wipe
- shared title position
- timeline advance
- map zoom or pan
- line/path continuation
- image pan between chapters
- chapter number scale and settle

Avoid random transition types on every slide.

## Interaction Patterns

- tabs: compare scenarios or audiences
- toggles: before/after, risk/control, current/future
- click-to-reveal: argument steps or teaching moments
- hover/focus labels: dense diagrams or maps
- animated counters: key numbers with clear units
- mini index: jump to sections in long decks

Do not make interaction necessary to read essential content unless the deck is being used live and the presenter controls it.

## Timing

- reveal duration: 450-900ms
- slide transition: 500-1000ms
- stagger: 80-160ms
- count-up: 700-1400ms

Disable complex motion for `prefers-reduced-motion`.

## DOM Conventions

Use predictable attributes so future agents can extend the deck:

```html
<section class="slide" data-slide data-transition="wipe">
  <h2 data-reveal>Title</h2>
  <div data-reveal data-delay="1">Evidence</div>
  <button data-toggle="scenario">Scenario</button>
</section>
```

Prefer CSS classes and small JavaScript. Use heavier animation libraries only when explicitly requested or already available.
