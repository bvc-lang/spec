# BVC format overview (v0.0.5 draft)

**Human name:** BVC — Basis · Vector · Goal  
**Extension:** `.bvc`.
**Legacy readable extension:** `.step` (compatibility alias; new writes use `.bvc`).

## Atom shape

```
#Name@en<[
Basis:
  - context
Vector:
  - action
Goal:
  - telos

Labels:
  atom.profile: work_item
  trace.status: pending
]>
```

## Multilingual (Detect-or-Declare)

Priority: `#Name@lang` → `Labels.lang` → `#!bvc lang=xx` → auto-detect first BVC key → `en`.

One dialect per atom. Mixed keys = `E_BVC_DIALECT_MIX`.

Registered dialects in this package:

- `en` — canonical section titles: `Basis`, `Vector`, `Goal`, `Labels`
- `ru` — registered section titles: `Базис`, `Вектор`, `Цель`, `Метки`

Optional section titles are also dialect-localized:

- `checks`: `Checks` / `Проверки`
- `evidence`: `Evidence` / `Свидетельства`
- `analysis`: `Analysis` / `Анализ`
- `decision`: `Decision` / `Решение`
- `uiRefs`: `UI_References` / `Референсы_UI`

## Draft schema

`schemas/bvc-atom-draft.v1.json` defines the structured authoring boundary used by formatters and LLM tools.

Core fields:

- `profile`, `name`, `basis`, `vector`, `goal`
- optional `labels`, `lang`, `checks`, `evidence`
- optional `structuredEvidence[]` as a machine-readable companion to prose evidence

`structuredEvidence[]` records are intentionally optional in the draft schema so existing atoms remain valid. Implementations may make structured evidence required for stricter task or gate tiers.

## Lints and compatibility

- `E_BVC_DIALECT_MIX`: one atom mixes BVC section keys from multiple dialects.
- `E_BVC_DIALECT_LANG_MISMATCH`: declared/resolved `lang` disagrees with section keys.
- `W_BVC_LANG_FALLBACK_EN`: no dialect declaration or detectable section key; parser falls back to `en`.
- `W_BVC_LEGACY_STEP_EXTENSION`: `.step` file path is readable but legacy.

## Artifacts in this package

- `dialects/*.json` — localized BVC section titles
- `schemas/bvc-atom-draft.v1.json` — LLM intermediate JSON

## Status

Published on npm as `@bvc-lang/spec`. Reference parser/linter: `@bvc-lang/cli`.
