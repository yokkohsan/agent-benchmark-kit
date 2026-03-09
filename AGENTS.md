# AGENTS.md

This file defines how AI coding agents (e.g. Codex CLI) should operate in this repository.

## Repository purpose

This repository contains **benchmark definitions**, not the system-under-test.

Agents should treat this repository as:

- a dataset of benchmark tasks
- a history of benchmark results
- documentation for evaluation methodology

Agents should **not implement agent systems here**.

---

## Operating model

Current benchmark workflow:

1. Tasks are defined in `tasks/` as YAML.
2. Benchmark execution is **manual or human-assisted**.
3. Results are stored in `results/` as JSON.
4. Each benchmark run is recorded as a new result file.

Automation may be added later, but **do not introduce it unless explicitly requested**.

---

## File conventions

Benchmark tasks:

tasks/*.yaml

Benchmark results:

results/*.json

Tasks must remain:

- stable
- human-readable
- version-controlled

Do **not regenerate tasks automatically**.

---

## Editing principles

When modifying this repository:

- Prefer small, reviewable commits.
- Avoid unnecessary structural changes.
- Do not introduce complex infrastructure.
- Maintain compatibility with existing task definitions.

Benchmark definitions should remain **simple and portable**.

---

## Supporting documents

Additional policies and formats are described in:

- docs/benchmark-policy.md
- docs/result-format.md
- BENCHMARK_SPEC.md

Agents should read those files before proposing structural changes.

---

## Current priority

1. Improve benchmark task definitions.
2. Add a small number of real-world tasks.
3. Keep results consistent across runs.

Automation and tooling are secondary priorities.
