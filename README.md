## MinChan Lee — putting LLMs into production

Selected excerpts from systems I've built and run. Each repository keeps the part where the engineering decisions were made, runs on its own, and says in its README what was left out.

The common thread: **let the model judge, and make everything that must hold regardless of what it decides — order, limits, idempotency, consent, the final decision — deterministic code.**

| | What it is | What to look at |
|---|---|---|
| [**dapalette-agent-runtime**](https://github.com/MinChanLee/dapalette-agent-runtime) | Runtime under an agent that runs influencer-marketing campaigns end to end — outreach, contracts, shipping, content review, payments | Deterministic control plane, leased workers, idempotency and owner approval enforced by the schema; a `demo.py` that replays a whole campaign without double-sending anything |
| [**reallang-speaking-engine**](https://github.com/MinChanLee/reallang-speaking-engine) | Scoring engine of a language-learning app: is a spoken attempt good enough? | Rules measure fluency, an LLM judges accuracy from text only, the engine decides; a judge rubric designed around asymmetric error costs and a regression eval built from real mis-grades |
| [**agentic-dag**](https://github.com/MinChanLee/agentic-dag) | Declarative DAG framework for multi-step LLM pipelines, used across six client automations | YAML nodes, layers computed by topological sort and run in parallel, operators separated from orchestration (designed by me, first implemented by Jeonggon Kim) |
