# @mastra/deepeval

## 0.1.0-alpha.0

### Minor Changes

- Added the `@mastra/deepeval` observability exporter to send Mastra traces to Confident AI for evaluation and monitoring. ([#20599](https://github.com/mastra-ai/mastra/pull/20599))

  Register it in your Mastra observability config:

  ```typescript
  import { Mastra } from '@mastra/core';
  import { Observability } from '@mastra/observability';
  import { DeepEvalExporter } from '@mastra/deepeval';

  export const mastra = new Mastra({
    observability: new Observability({
      configs: {
        deepeval: {
          serviceName: 'my-service',
          exporters: [new DeepEvalExporter()],
        },
      },
    }),
  });
  ```

  Set `CONFIDENT_API_KEY` (and optionally `CONFIDENT_TRACE_ENVIRONMENT`) to send traces. Mastra spans map to Confident AI's `AGENT`, `LLM`, `TOOL`, `RETRIEVER`, and `CUSTOM` span types, with model, token counts, tool calls, and metric collections carried through.

### Patch Changes

- Updated dependencies [[`1f7bbd7`](https://github.com/mastra-ai/mastra/commit/1f7bbd7785a8d230aad02454ecabeb4a0b2cc96f)]:
  - @mastra/core@1.56.1-alpha.1
