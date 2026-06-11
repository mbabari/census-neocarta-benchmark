# Publishing this repo to GitHub

Use this checklist before pushing a **public or shared** repository.

## Never commit

- `.env` (contains API keys and passwords) — already in `.gitignore`
- `semantic-layer-slack-summary.md` or other internal Slack/meeting notes
- `curl-test.txt`, `*.stderr.log`, local scratch files
- GCP project IDs or personal emails hardcoded in code (use `.env` instead)

Copy `.env.example` → `.env` locally; colleagues do the same with **their** credentials.

## Recommended: Census-focused first push

From `semantic-layer-workshop/`:

```bash
git add .env.example .gitignore README.md pyproject.toml uv.lock
git add module-2/build_census_semantic_layer.py
git add module-3/CENSUS_README.md module-3/census_demo_findings.md
git add module-3/census_agent.py module-3/census_agent_optimized.py
git add module-3/benchmark_census.py
# optional utilities
git add module-3/schema_scaling.py module-3/measure_tokens.py
git status   # review before commit
```

Optional workshop extras (ACME agent, Spider2, StackOverflow scripts) can follow in a
second commit if you want the full workshop + Census extension in one repo.

## Create the GitHub repo

```bash
# new remote (replace with your org/repo)
git remote add census-fork git@github.com:YOUR_ORG/census-neocarta-benchmark.git
git push -u census-fork main
```

Or fork from [neo4j-field/semantic-layer-workshop](https://github.com/neo4j-field/semantic-layer-workshop)
and push the Census extension as a branch.

## If keys were ever exposed

Rotate `OPENAI_API_KEY`, `ANTHROPIC_API_KEY`, and Neo4j passwords before sharing the repo.
