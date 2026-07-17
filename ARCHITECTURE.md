# Hardware-Detached Agent Runtime

## Canonical definition

A storage-rooted, proof-carrying runtime for persistent AI agents. An agent suspends into a signed provider-neutral capsule, releases active execution resources, wakes through the same stable SSH identity on fresh compatible compute, recovers its workspace, objectives, authority, and evidence chain, continues unfinished work, and collapses back into storage when idle.

## System boundary

```text
User or SSH session
→ agent resolver
→ macOS inference produces typed plan
→ policy engine authorizes capabilities
→ isolated Linux runtime executes
→ verifier observes results
→ receipt enters capsule history
```

The model plane, control plane, execution provider, and suspension store are logically separate even when they occupy one M5 Pro.

## State classes

1. **Immutable:** model identifiers, runtime images, tool schemas, and policy versions.
2. **Durable agent:** objectives, commitments, working summaries, task boundaries, and continuation instructions.
3. **Mutable workspace:** files, repository changes, generated artifacts, and execution outputs.
4. **Ephemeral acceleration:** KV caches, tensors, compiled kernels, scheduler internals, and process memory.
5. **Evidence:** commands, decisions, grants, file hashes, verification, lineage, and signatures.

Provider-neutral restoration requires durable agent, workspace, and evidence state. Ephemeral acceleration state may be discarded.

## Safety invariants

- Suspension occurs only at a semantic boundary with known external-effect status.
- A manifest is atomically sealed or invalid; a partial checkpoint is never current.
- A wake lease prevents concurrent restoration of the same lineage epoch.
- Rollback, corruption, unauthorized forks, and duplicated capsules are rejected.
- Authority may be preserved or reduced, but never silently increased.
- Every restore receipt declares exact, semantic, or degraded restoration.

## Proof model

Receipts cover observable transitions rather than hidden model reasoning. Each receipt commits to agent identity, capsule hash, runtime image, typed operation, policy decision, exit status, output hashes, filesystem-delta root, verification result, timestamp, parent receipt hash, and signature.

## First implementation

The first implementation proves a single transition deeply: an operational agent reaches semantic quiescence, seals into signed storage, loses its original runtime, transfers to a genuinely separate compatible environment, wakes under the same SSH identity, verifies its lineage and attenuated capabilities, and continues the declared task without full prompt replay.
