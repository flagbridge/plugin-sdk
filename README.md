# FlagBridge Plugin SDK

Build plugins for [FlagBridge](https://github.com/flagbridge/flagbridge).

> **Note:** Active development happens in the [monorepo](https://github.com/flagbridge/flagbridge/tree/main/packages/plugin-sdk). This repo is used for distribution and issue tracking.

## Installation

```bash
npm install @flagbridge/plugin-sdk
# or
pnpm add @flagbridge/plugin-sdk
```

## Quick Start

```typescript
import { definePlugin } from '@flagbridge/plugin-sdk';

export default definePlugin({
  manifest: {
    name: 'my-plugin',
    version: '1.0.0',
    description: 'My FlagBridge plugin',
    author: 'Your Name',
    hooks: ['onFlagEvaluated'],
  },
  async onFlagEvaluated(ctx, flagKey, value) {
    // React to flag evaluations
  },
});
```

## Documentation

Full docs at [flagbridge.io/docs/plugins](https://flagbridge.io/docs/plugins)

## License

Apache 2.0
