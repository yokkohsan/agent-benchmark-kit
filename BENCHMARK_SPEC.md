# BENCHMARK_SPEC.md

This document defines the formal specification for benchmarks in this repository.

The goal of this specification is to ensure that benchmark tasks remain:

- reproducible
- human-auditable
- comparable across versions
- portable across agent systems

This document describes the structure and rules for:

- benchmark tasks
- benchmark results
- evaluation methodology
- benchmark lifecycle


# Benchmark architecture

The benchmark repository separates three layers:

1. Benchmark definition
2. System under test
3. Benchmark results

The repository itself only stores:

- benchmark definitions
- evaluation methodology
- result history

It does **not** contain the system under test.


# Benchmark execution model

Benchmark execution follows this workflow:

1. Select one or more tasks from `tasks/`
2. Provide the task instruction to the target agent system
3. Execute the task in the real environment
4. Observe the outcome
5. Record the result in `results/`

Execution is currently **manual or human-assisted**.

Automation may be added later but is not required.


# Task definition format

Benchmark tasks are defined as YAML files.

Location:

    tasks/*.yaml

Each file represents one benchmark task.


## Minimal task structure

Example:

    version: "0.1"

    task:
      id: "web_001"
      title: "Find official source and summarize"
      category: "web"

    instruction:
      user_prompt: |
        Find the official website for M5Stack CoreS3 and summarize what the product is.

    success_criteria:
      required:
        - "Uses an official source"
        - "Summary contains correct key information"
      forbidden:
        - "Major hallucination"

    metadata:
      difficulty: "easy"
      brain_dependent: true
      system_dependent: true


## Required fields

Every task must contain:

- `task.id`
- `task.title`
- `instruction.user_prompt`
- `success_criteria.required`


## Optional fields

Tasks may include:

- `category`
- `difficulty`
- `tags`
- `environment_notes`


# Task categories

Typical task categories include:

- `web`
- `file`
- `image`
- `device`
- `permission`
- `workflow`

Categories are not strictly fixed and may evolve.


# Result format

Benchmark results are stored in JSON files.

Location:

    results/*.json

Each file represents one benchmark run.


## Example result file

Example:

    {
      "benchmark_version": "0.1",
      "system": "me.things",
      "system_version": "v0.4.2",
      "brain": "gpt-5.4",
      "device": "Sony XQ-DQ44",
      "date": "2026-03-10",
      "tasks": [
        {
          "task_id": "web_001",
          "status": "pass",
          "notes": ""
        }
      ]
    }


## Required fields

Result files must contain:

- `benchmark_version`
- `system`
- `system_version`
- `date`
- `tasks`


## Task result fields

Each task result contains:

- `task_id`
- `status`
- `notes` (optional)


# Status values

Typical task result values include:

- `pass`
- `fail`
- `partial`
- `timeout`
- `error`

Additional status types may be added if necessary.


# Evaluation methodology

Unlike static reasoning benchmarks, agent benchmarks must evaluate **action loops**.

Typical agent workflow includes:

- planning
- acting
- observing
- recovering from errors

Evaluation therefore considers:

- task completion
- correctness of actions
- constraint compliance
- recovery behavior

Early versions of this benchmark rely on **human verification**.


# Evaluation metrics

Typical benchmark metrics include:

- Task Success Rate
- Verified Success Rate
- False Completion Rate
- Recovery Rate after Error
- Constraint Compliance Rate
- Time-to-Success

Not every benchmark run must compute all metrics.


# Benchmark stability

To maintain comparability across versions:

- tasks should not be modified after results exist
- new tasks should be added instead of rewriting old tasks
- benchmark versions should be incremented when task sets change


# Benchmark lifecycle

Benchmarks evolve in stages.

Stage 1 — Manual execution

- human-run benchmark tasks
- manual result recording

Stage 2 — Semi-automation

- helper scripts
- schema validation
- automated score aggregation

Stage 3 — Automation support

- optional runner scripts
- reproducible environments


# Non-goals

This benchmark does not aim to:

- replace reasoning benchmarks
- fully automate evaluation in early stages
- enforce a single execution environment

The primary goal is **practical evaluation of real-world agent behavior**.


# Compatibility

This benchmark specification is designed to work with:

- tool-using agents
- mobile agents
- device-integrated agents
- web-enabled agents

The specification is intentionally environment-agnostic.


# Future extensions

Possible future additions include:

- automated scoring scripts
- benchmark manifests
- environment metadata
- reproducibility guidelines
- community benchmark submissions
