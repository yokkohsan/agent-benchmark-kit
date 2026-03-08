# agent-benchmark-kit

A practical benchmark repository for autonomous / tool-using agents.

This repository is designed to record stable, repeatable benchmark tasks and results across agent systems, brains, versions, and devices.

It is intentionally lightweight at the beginning:
- manual execution
- manual result collection
- versioned task definitions
- versioned benchmark results

The goal is to create a benchmark that remains meaningful even if the underlying model changes over time.

## Why this repository exists

Modern agent systems are evaluated by more than abstract reasoning alone.

For practical use, we often care about:

- task success
- verified success
- false completion
- recovery after error
- permission handling
- constraint compliance
- execution stability across versions

This repository is meant to preserve those measurements in a stable and comparable form.

## Scope

This repository is intended for autonomous or semi-autonomous agent systems, including but not limited to:

- me.things
- other tool-using chat agents
- mobile agents
- web agents
- device-integrated agents

The repository is benchmark-oriented, not implementation-oriented.

That means:

- the benchmark definitions live here
- the agent system under test lives elsewhere
- the results are recorded here

## Initial operating model

At the beginning, benchmark execution is intentionally manual.

Typical flow:

1. Select one or more benchmark tasks from `tasks/`
2. Ask the target agent system to execute them
3. Observe the outcome
4. Record the results in `results/`
5. Commit the result files

This keeps the benchmark definition stable while allowing flexible early-stage iteration.

## Design principles

### 1. Stable benchmark definition

Benchmark tasks should not be regenerated ad hoc by the tested agent.  
The benchmark definition should remain fixed and version-controlled.

### 2. Separation of benchmark and system-under-test

This repository stores:

- tasks
- schemas
- scoring rules
- benchmark results

It should not become tightly coupled to one implementation.

### 3. Human-auditable results

At least in the early phase, results should be understandable and reviewable by humans.

### 4. Long-term comparability

The benchmark should remain useful even when:

- the model changes
- the app version changes
- the device changes
- the execution environment changes

## Planned structure

The basic idea is:

- `tasks/` → benchmark task definitions
- `results/` → recorded benchmark runs
- `schemas/` → JSON/YAML schemas for tasks and results
- `scripts/` → helper scripts for validation, aggregation, or reporting
- `docs/` → benchmark policy, scoring notes, and contributor guidance

## Benchmark categories

The initial benchmark is expected to focus on practical agent behavior such as:

- file operations
- web search and summarization
- image understanding
- device API interaction
- permission-required retry flow
- honest failure reporting
- multi-step end-to-end tasks

These categories may expand later.

## Example metrics

Typical metrics may include:

- Task Success Rate
- Verified Success Rate
- False Completion Rate
- Permission Handling Success Rate
- Recovery Rate after Error
- Constraint Compliance Rate
- Time-to-Success

Not every benchmark run needs every metric at the start.

## Result philosophy

A benchmark result should clearly record at least:

- benchmark task ID
- target system name
- target system version
- brain / model
- device or environment
- execution date
- outcome
- notes

The benchmark should preserve not only scores but also context.

## Intended evolution

This repository is expected to evolve in phases:

### Phase 1

- manual execution
- manual result recording

### Phase 2

- helper scripts
- schema validation
- score aggregation

### Phase 3

- semi-automated execution support
- issue-template-based community submissions

### Phase 4

- broader automation, where appropriate

## Non-goals

At least initially, this repository does not aim to:

- fully automate every benchmark run
- replace implementation-level unit tests
- measure only abstract reasoning
- optimize for a single model or a single app

## Contributing

In the early stage, contributions may include:

- proposing benchmark tasks
- reporting benchmark results
- improving schemas
- clarifying scoring rules
- improving documentation

## Status

This repository is in an early design stage.

The immediate priority is:

1. define a small practical benchmark set
2. make result recording consistent
3. preserve version-to-version comparability

## License

This repository is released under the MIT License.  
See the [LICENSE](LICENSE) file for details.
