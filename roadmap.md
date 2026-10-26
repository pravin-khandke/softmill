# Roadmap

Ordered by what can catch a false claim soonest, not by what is interesting to build.

## 1. The verifier over git and one CI provider

The smallest thing that catches the common lie: an agent reporting a passing test run that did not pass.

- read the commit and its diff from git
- read the CI result for that commit from the provider's API
- compare declared test outcomes with the CI artifact
- emit a pack with every field labelled derived or declared

## 2. Cost recomputation

- token counts from the provider response, not from the agent's span
- a dated pricing table, committed, so a pack can be recomputed later
- mismatch between declared and recomputed cost is a finding

## 3. Approval binding

- approval recorded against a hash of the specific action
- verification that the action executed is the action approved
- a stale or widened approval is a refusal, not a warning

## 4. Signed, replayable packs

- hash chained packs
- a replay command that reproduces the pack from the sources

## Explicitly not next

- a hosted service
- a model in the verification path
- dashboards
