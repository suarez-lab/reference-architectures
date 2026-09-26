# Reference Architectures

**English** · [Español](README.es.md)

Shapes we have built more than once, with the trade-off written down rather than implied.

Each one states what it optimises for, what it costs, and when **not** to use it. An
architecture note without a "when not to use this" section is marketing.

| Pattern | Optimises for | Main cost |
| --- | --- | --- |
| [AI-last pipeline](ai-last-pipeline.md) | Cost per request; prompt-injection surface | A rules layer you must maintain |
| [Bounded autonomous loop](bounded-autonomous-loop.md) | Safety of unattended iteration | Friction at every turn |
| [Alerting on the fallback path](alert-on-the-fallback-path.md) | Detecting silent degradation | More alerts to keep honest |
