# AGENTS.md

## Repo purpose
- This repository is a benchmark-definition repository.
- It is not the system-under-test.

## Operating model
- In the early phase, prefer manual execution and manual result recording.
- Do not introduce automation unless explicitly requested.

## Data conventions
- Benchmark task definitions should be written in YAML.
- Benchmark results should be recorded in JSON.

## Editing principles
- Prefer small, reviewable changes.
- Do not over-engineer the repository structure.
- Keep benchmark definitions stable and human-auditable.
- Do not change task semantics unless explicitly requested.

## Current priority
- Improve the benchmark definition structure first.
- Add a small number of practical benchmark tasks before adding scripts or CI.
