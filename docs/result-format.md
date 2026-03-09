# Benchmark Result Format

Benchmark results are stored in `results/` as JSON files.

Each file represents one benchmark run.

## Example structure

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

## Fields

benchmark_version  
Version of the benchmark task set.

system  
Name of the agent system.

system_version  
Version of the system under test.

brain  
Underlying model used by the system.

device  
Execution environment.

date  
Date when the benchmark run was executed.

tasks  
Results for individual tasks.

## Task result fields

task_id  
Identifier of the benchmark task.

status  
Outcome of the task.

notes  
Optional notes describing observations or issues.

## Status values

Typical task status values:

- pass
- fail
- partial
- timeout
- error
