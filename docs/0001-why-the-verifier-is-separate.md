# 0001 Why the verifier is separate from the factory

Date: 2026-10-25
Status: accepted

## Context

The obvious build is one system that runs the work and also reports on it. That is what every agent
harness does today, and it is the reason their logs are unusable as evidence. The component that
produces a claim cannot also be the component that validates it.

## Decision

The factory and the verifier are separate components, and the verifier reads only from systems the
worker cannot write. In practice: git objects, the CI provider's result API, the pricing table in this
repository, the approval store, and the target system's own record of the effect.

## Consequences

- The factory can be replaced, rewritten or abandoned without invalidating a single evidence pack.
- The verifier needs credentials to read source systems. That is a real operational cost.
- Some claims will be `unverifiable` because no system of record exists for them. Reporting that
  honestly is the point, and inventing a derived value from the agent's own span is not allowed.
