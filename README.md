# agent-benchmark-kit

A practical benchmark repository for autonomous / tool-using agents.

This repository is designed to record stable, repeatable benchmark tasks and results across agent systems, brains, versions, and devices.

It is intentionally lightweight at the beginning:

- manual execution
- manual result collection
- versioned task definitions
- versioned benchmark results

The goal is to create a benchmark that remains meaningful even if the underlying model changes over time.

---

# Background

Recent research on AI agents highlights that evaluating an agent requires more than traditional LLM benchmarks such as MMLU, GSM8K, or ARC-style reasoning tests.

Many modern agent benchmarks focus on environments and tool use rather than isolated question–answer tasks.

Examples include:

- **GAIA** – multi-step real-world reasoning tasks  
- **WebArena** – browser-based environment interaction  
- **OSWorld / AndroidWorld** – operating system and mobile task environments  
- **MobileWorld** – real-world smartphone workflows  

However, most existing benchmarks rely on specialized infrastructure such as Dockerized environments, simulators, or controlled sandboxes.

This repository explores a complementary approach:

- evaluate agents **in real execution environments**
- run tasks manually or semi-manually on real systems
- record results in a stable, versioned dataset

The goal is not to replace research benchmarks but to provide a **practical benchmark layer** for real-world agent systems.

In particular, this repository aims to support evaluation of agents that interact with:

- web resources
- local files
- device APIs
- system permissions
- multi-step workflows

Such systems are increasingly common in tool-using or device-integrated agents, yet they are still underrepresented in existing evaluation suites.

This repository therefore focuses on **real-world task evaluation** rather than purely simulated environments.

---

# Benchmark positioning

Agent benchmarks today broadly fall into three categories.

## Reasoning benchmarks

Examples:
- ARC-AGI
- MMLU
- GSM8K

These evaluate model reasoning on static question–answer tasks but do not measure tool use or real-world interaction.

## Environment benchmarks

Examples:
- WebArena
- OSWorld
- AndroidWorld

These evaluate agents inside controlled environments such as browsers, virtual machines, or emulators.

While powerful, these benchmarks often require heavy infrastructure and specialized runtime environments.

## Real-world task benchmarks

This repository explores a lightweight alternative:

- tasks are defined as portable specifications
- execution occurs in real environments
- results are recorded and versioned

Rather than simulating the world, the benchmark runs in the **actual execution environment of the agent system**.

This approach is particularly useful for evaluating:

- tool-using agents
- device-integrated agents
- mobile agents
- real-world automation systems

---

# What makes this benchmark different

This repository intentionally takes a different approach from many research benchmarks.

Key characteristics include:

**Real execution environments**

Tasks are executed in the real environment where the agent normally operates, rather than in a simulated or containerized environment.

**Minimal infrastructure**

No specialized sandbox, VM, or Docker environment is required to begin running benchmarks.

**Human-auditable evaluation**

Early phases prioritize human review and verification rather than fully automated scoring systems.

**Portable task definitions**

Benchmark tasks are defined as portable YAML specifications that can be used across multiple agent systems.

**Long-term comparability**

Results are recorded in a simple, versioned format so that performance changes across models, devices, or system versions can be compared over time.

---

# Evaluation philosophy

Agent evaluation differs fundamentally from traditional static benchmarks.

Instead of measuring only whether an answer is correct, agent systems must be evaluated across an entire **action loop**:

- planning
- acting
- observing
- recovering from errors

For this reason, this benchmark emphasizes metrics such as:

- task success
- verified success
- false completion
- recovery after error
- constraint compliance
- time-to-success

Early versions of this benchmark intentionally include **human-in-the-loop verification**.

While automated scoring is desirable in later phases, human verification provides higher reliability during the early design stage and helps ensure that benchmark definitions remain meaningful and interpretable.

---

# Scope

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

---

# Initial operating model

At the beginning, benchmark execution is intentionally manual.

Typical flow:

1. Select one or more benchmark tasks from `tasks/`
2. Ask the target agent system to execute them
3. Observe the outcome
4. Record the results in `results/`
5. Commit the result files

This keeps the benchmark definition stable while allowing flexible early-stage iteration.

---

# Design principles

## Stable benchmark definition

Benchmark tasks should not be regenerated ad hoc by the tested agent.  
The benchmark definition should remain fixed and version-controlled.

## Separation of benchmark and system-under-test

This repository stores:

- tasks
- schemas
- scoring rules
- benchmark results

It should not become tightly coupled to one implementation.

## Human-auditable results

At least in the early phase, results should be understandable and reviewable by humans.

## Long-term comparability

The benchmark should remain useful even when:

- the model changes
- the app version changes
- the device changes
- the execution environment changes

---

# Planned structure

The repository is organized as follows:

- `tasks/` → benchmark task definitions  
- `results/` → recorded benchmark runs  
- `schemas/` → JSON/YAML schemas for tasks and results  
- `scripts/` → helper scripts for validation, aggregation, or reporting  
- `docs/` → benchmark policy, scoring notes, and contributor guidance  

See [BENCHMARK_SPEC.md](BENCHMARK_SPEC.md) for the formal benchmark specification.

---

# Benchmark categories

The initial benchmark is expected to focus on practical agent behavior such as:

- file operations
- web search and summarization
- image understanding
- device API interaction
- permission-required retry flow
- honest failure reporting
- multi-step end-to-end tasks

These categories may expand later.

---

# Example metrics

Typical metrics may include:

- Task Success Rate
- Verified Success Rate
- False Completion Rate
- Permission Handling Success Rate
- Recovery Rate after Error
- Constraint Compliance Rate
- Time-to-Success

Not every benchmark run needs every metric at the start.

---

# Intended evolution

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

---

# Non-goals

At least initially, this repository does not aim to:

- fully automate every benchmark run
- replace implementation-level unit tests
- measure only abstract reasoning
- optimize for a single model or a single app

---

# Contributing

In the early stage, contributions may include:

- proposing benchmark tasks
- reporting benchmark results
- improving schemas
- clarifying scoring rules
- improving documentation

---

# Status

This repository is in an early design stage.

The immediate priority is:

1. define a small practical benchmark set  
2. make result recording consistent  
3. preserve version-to-version comparability  

---

# References

Examples of agent benchmarks and evaluation research:

- [GAIA Benchmark](https://huggingface.co/gaia-benchmark)
- [WebArena](https://webarena.dev)
- [OSWorld](https://os-world.github.io)
- [AndroidWorld](https://androidworld.dev)
- [MobileWorld](https://github.com/google-research/mobileworld)
- [AI Agent Benchmark Compendium](https://github.com/philschmid/ai-agent-benchmark-compendium)
- [8 Benchmarks Shaping the Next Generation of AI Agents](https://tessl.io/blog/8-benchmarks-shaping-the-next-generation-of-ai-agents/)
- [Top Agentic Evaluation Benchmarks (2025)](https://o-mega.ai/articles/top-10-agentic-evals-benchmarking-actionable-ai-2025)
- [AI Agent Benchmarks Overview](https://www.evidentlyai.com/blog/ai-agent-benchmarks)

---

## License

This repository is released under the MIT License.  
See the [LICENSE](LICENSE) file for details.
