# Google ADK 2.0 Graph Workflows — Code Examples

Example code for the **graph workflows** (declarative, edge-based agent orchestration) introduced in Google ADK 2.0.

- 📖 Article: [Google ADK 2.0 Graph Workflows: A Complete Guide with Code Examples](https://medium.com/google-cloud/google-adk-2-graph-workflows-a-complete-guide-with-code-examples-7e27046b85d5) — by **Romin Irani**
- 💻 Source repository: [rominirani/adk-workflow-patterns](https://github.com/rominirani/adk-workflow-patterns)
- 📰 Full article as PDF: [`Google_ADK_2_Graph_Workflows_Article.pdf`](Google_ADK_2_Graph_Workflows_Article.pdf)

This repo is a standalone mirror of the `graph-workflows/examples/` folder from the source repo, so the article's examples live in one focused place. All code is by Romin Irani; see the [source repo](https://github.com/rominirani/adk-workflow-patterns) for the full context (collaborative workflows, memory guide, and other guides).

## Examples

| # | File | Pattern |
|---|------|---------|
| 01 | [`examples/01_sequential.py`](examples/01_sequential.py) | Sequential pipeline: extract data → format prompt → summarize agent (password-reset inquiry) |
| 02 | [`examples/02_routing.py`](examples/02_routing.py) | Conditional routing: a router node classifies the query and routes to billing, shipping, or general agents |
| 03 | [`examples/03_parallel_join.py`](examples/03_parallel_join.py) | Parallel fan-out: three fetchers (profile, orders, account) run concurrently and merge via a `JoinNode` |
| 04 | [`examples/04_full_pipeline.py`](examples/04_full_pipeline.py) | Full pipeline: parallel DB fetches + join, then classification and routing to billing or tech support |
| 05 | [`examples/05_nested.py`](examples/05_nested.py) | Nested workflows: a sub-workflow embedded as a node inside a main workflow |
| 06 | [`examples/06_loop.py`](examples/06_loop.py) | Loop with conditional exit: a drafter–critic loop that retries until the critic approves |
| 07 | [`examples/07_hitl.py`](examples/07_hitl.py) | Human-in-the-loop: high-value refunds pause for human approval before proceeding |
| 08 | [`examples/08_dynamic.py`](examples/08_dynamic.py) | Dynamic node: an `@node` function that runs an agent in a loop via `ctx.run_node` |
| 09 | [`examples/09_complete_system.py`](examples/09_complete_system.py) | Complete customer support system combining all patterns: parallel fetchers + join, dynamic routing, troubleshooting loop, HITL approval, specialist agents |

## Setup & Run

Requires **Python 3.10+** and Google ADK 2.6+ (see `requirements.txt`).

```bash
# 1. Create and activate a virtual environment
python3 -m venv .venv
source .venv/bin/activate

# 2. Install dependencies
pip install -r requirements.txt

# 3. Set your model credentials
export GOOGLE_API_KEY="your-api-key"      # AI Studio key, or
export GOOGLE_GENAI_USE_VERTEXAI=1        # Vertex AI
# export GOOGLE_CLOUD_PROJECT=...         # if using Vertex AI
# export GOOGLE_CLOUD_LOCATION=...

# 4. Run an example
python examples/01_sequential.py
```

Model override: all examples read the model from the `ADK_MODEL` environment variable (default `gemini-2.5-flash`):

```bash
ADK_MODEL="gemini-2.5-flash" python examples/02_routing.py
```

## Notes

- Examples are copied verbatim from the source repo's `graph-workflows/examples/`; no modifications were made.
- The default entry point in each file is `main()`, so each script runs end-to-end with `python examples/<file>`.
- Licensed under the terms of the [source repo](https://github.com/rominirani/adk-workflow-patterns).
