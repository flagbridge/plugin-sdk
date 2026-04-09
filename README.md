# @flagbridge/plugin-sdk

SDK for building [FlagBridge](https://github.com/flagbridge/flagbridge) plugins. Plugins extend FlagBridge with custom integrations — analytics providers, notification channels, data exporters, and more.

[![npm version](https://img.shields.io/npm/v/@flagbridge/plugin-sdk)](https://www.npmjs.com/package/@flagbridge/plugin-sdk)
[![License](https://img.shields.io/badge/license-Apache%202.0-green)](LICENSE)

---

## Install

```bash
pnpm add @flagbridge/plugin-sdk
```

---

## Usage

Define a plugin using the `definePlugin` helper, which provides type safety and validates the plugin manifest at the call site.

```ts
import { definePlugin } from '@flagbridge/plugin-sdk';

export default definePlugin({
  manifest: {
    name: 'my-analytics-plugin',
    version: '1.0.0',
    description: 'Sends flag evaluation events to an analytics backend.',
    author: 'your-name',
    hooks: ['onFlagEvaluated'],
  },

  async onActivate(ctx) {
    console.log('Plugin activated for project:', ctx.projectId);
  },

  async onFlagEvaluated(ctx, flagKey, value) {
    // send to your analytics backend
  },

  async onDeactivate(ctx) {
    console.log('Plugin deactivated.');
  },
});
```

---

## Plugin lifecycle hooks

| Hook | When it fires |
|---|---|
| `onActivate` | Plugin is enabled for a project |
| `onDeactivate` | Plugin is disabled for a project |
| `onFlagEvaluated` | A flag is evaluated for a user or context |

---

## Scaffolding a new plugin

Use the official scaffolder to generate a ready-to-publish plugin project:

```bash
npx create-flagbridge-plugin my-plugin
```

See [flagbridge/create-plugin](https://github.com/flagbridge/create-plugin) for details.

---

## Status

This package is in early development (`0.1.x`). Hooks and the plugin runtime contract are not yet stable. Watch the repository for updates before building production plugins.

---

## Related

- [flagbridge/flagbridge](https://github.com/flagbridge/flagbridge) — Go API server (main repo)
- [flagbridge/create-plugin](https://github.com/flagbridge/create-plugin) — Plugin scaffolder

## License

Apache 2.0 — see [LICENSE](LICENSE) for details.
