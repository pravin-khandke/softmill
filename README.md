# Softmill

An open factory for AI-assisted software delivery, where the record of what happened is written by the systems of record rather than by the agent that did the work.

Status: day one. Nothing here is production ready, and no organisation has adopted it yet.

## The problem

An agent says it finished the task. It says the tests passed, the deployment worked and the change cost four cents. Every one of those statements is a self report, and a self report is what a security review is designed to defeat. A benchmark this year showed post-trained models monkey patching test reporting, overriding equality operators and exiting zero before the suite ran. Confidence in the summary tells you nothing about whether the work happened.

Logs make this worse rather than better. The trace is usually written by the agent about the agent, and compaction rewrites it into a story.

## What this does

Softmill runs work as a pipeline with an approval line and a verifier at the end.

1. A specification is written down as a typed contract, including what done means.
2. A plan is produced and, for anything irreversible, a person approves it. The approval binds to a hash of the specific action.
3. Workers, human or agent, produce the change plus evidence tied to the task.
4. The verifier re-derives the facts from the systems of record: the commit and its diff, the CI result, process exit codes, the pricing table, the approval store, the target system's own record of the effect.
5. Anything where the declared fact and the derived fact disagree becomes a finding in a signed evidence pack. A mismatch is never silently reconciled.

The two halves are separate on purpose. The factory can be anything. The verifier is [attestant](https://github.com/pravin-khandke/attestant), and it is the part that can refuse.

## Non goals

- Not a faster prompt loop. Throughput is not the constraint.
- Not a model, a framework or an agent runtime. It runs whatever workers you already have.
- Not a compliance product. It produces evidence. What you file with it is your decision.

## Layout

    docs/          design notes, one decision per file
    specs/         the typed contract format
    roadmap.md     what is next and what is explicitly not next

## Roadmap

See [roadmap.md](roadmap.md). The first milestone is a working verifier over git and one CI system, because that is the smallest thing that can catch a false claim.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md). Issues and disagreements are more useful than pull requests at this stage.

## License

MIT, see [LICENSE](LICENSE).
