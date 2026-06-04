# Template Selection Protocol

Use this when visual direction matters and the user has not already chosen a specific template.

## Principle

Do not pretend the agent has reliable taste. The agent should narrow options; the human should choose from real visual evidence.

This protocol is inspired by the `beautiful-html-templates` workflow: ask for occasion and mood, select three different candidates from metadata, generate title-slide previews with real content, then let the user choose before full production.

## Required Inputs

Collect or infer:

- occasion: where the deck will be used
- audience: who will see it
- mood: what it should feel like
- topic/title: real title for previews
- subtitle or context line: optional but helpful
- author/date/team: optional metadata for previews

If missing, ask only two questions first:

```text
这次演讲/汇报是什么场合？
你希望它是什么氛围：权威、克制、锋利、温暖、杂志感、科技感，还是更大胆？
```

If the user gave enough context, restate your inferred occasion and mood instead of asking again.

## Three-Candidate Rule

Pick exactly three visual directions unless the user asks for more.

The three candidates should be meaningfully different:

- Safe fit: most likely to work for the audience.
- Expressive fit: more memorable but still appropriate.
- Wildcard: a sharper or unexpected direction that may unlock a better deck.

Do not offer three variants that are only color changes.

## Metadata Matching

When a template library has metadata, filter by:

- `mood`
- `tone`
- `occasion`
- `best_for`
- `avoid_for`
- `formality`
- `density`
- `scheme`
- slide count and available layout variety

Treat `occasion` as a soft signal. A founder-pitch template might work for a technical keynote if the mood and density fit.

## Preview Requirement

Before building the full deck, create title-slide previews for the three candidates when feasible.

Each preview must:

- use the user's real title
- use real subtitle/context when available
- include author/date/team metadata when useful
- preserve the candidate template's original visual language
- avoid invented placeholder claims
- be browser-openable

Save previews in a clear local folder such as:

- `outputs/<deck-name>-template-previews/`
- `previews/<deck-name>/`

Open or browser-check previews when possible before asking the user to choose.

## User Choice Prompt

After previews, ask for a visual choice in plain language:

```text
我做了 3 个封面方向：稳妥正式、锋利发布会、杂志叙事。你选一个最接近你想要的气质，我再按那一套视觉系统完整扩展全稿。
```

If the user cannot decide, choose the safe fit and explain why.

## When To Skip Preview

Skip preview only when:

- the user explicitly says to decide and proceed
- the task is urgent and small
- no browser or rendering path is available
- the deck already has a mandated brand/template

If skipped, state the chosen template/style and assumption in the final summary.
