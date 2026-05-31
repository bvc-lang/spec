# @bvc-lang/spec

**BVC** (Basis · Vector · Goal) — typed atom format for AI-agent context and durable intent.

Public file extension: **`.bvc`**.

## Package contents (v0.0.0 placeholder)

| Path | Description |
|---|---|
| `dialects/en.json`, `dialects/ru.json` | Registered dialect registry (Detect-or-Declare) |
| `schemas/bvc-atom-draft.v1.json` | LLM draft JSON schema (`lang`, BVC fields) |
| `spec/overview.md` | Spec overview + links to ADR |

## Related packages (roadmap)

- `@bvc/parser` — reference parser / linter
- `@bvc-lang/cli` — `bvc lint`, `bvc format`

## Governance

- Naming ADR: `.bvc` public canon (distinct from ISO 10303 STEP CAD exchange)
- Multilingual ADR: EN canonical + registered dialects, no inline aliases

## Install

```bash
npm install @bvc-lang/spec
```

```javascript
import spec from '@bvc-lang/spec';
import enDialect from '@bvc-lang/spec/dialects/en.json' with { type: 'json' };
```

## License

Apache-2.0 (this package). Specification text CC BY 4.0 when published on `bvc-lang/spec`.

## Links

- Work Graph pilot repo (implementation reference)
- AN-8 / AN-18 / AN-19 analytics (design history)
