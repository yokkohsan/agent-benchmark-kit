# Benchmark Policy

This document explains the evaluation philosophy behind this repository.

## Purpose

The goal of this benchmark is to evaluate **agent systems operating in real environments**.

Unlike many research benchmarks, this repository prioritizes:

- real execution contexts
- tool interaction
- device integration
- human-verifiable results

## Evaluation style

The benchmark currently uses **human-in-the-loop evaluation**.

Reasons:

- real-world environments are difficult to fully simulate
- early benchmark definitions require human judgment
- manual verification ensures higher reliability

Automation may be introduced gradually.

## Benchmark stability

Tasks should remain stable once introduced.

Avoid:

- rewriting tasks frequently
- changing success criteria after results are recorded
- regenerating tasks dynamically

Consistency across versions is essential.
