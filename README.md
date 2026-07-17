# Capsule Runtime

**A storage-rooted, proof-carrying runtime for persistent AI agents.**

An agent can suspend into a signed, provider-neutral capsule; release its active execution resources; wake through the same stable SSH identity on fresh compatible compute; recover its workspace, objectives, authority, and evidence chain; continue unfinished work; and collapse back into storage when idle.

The durable identity belongs to the capsule—not to a container, VM, process, cloud account, or physical computer.

## The first product has exactly one job

> Suspend a functioning agent into signed storage, destroy its original runtime, and restore it through the same SSH identity inside a newly materialized isolated environment—with its pending task, filesystem, permissions, and proof history intact.

This first version supports exact restoration on compatible environments and explicitly labeled semantic restoration elsewhere. It does not claim universal heterogeneous live migration, cross-ISA register translation, arbitrary GPU-kernel restoration, or deterministic replay across unrelated model providers.

## M5 Pro architecture

```text
macOS host
├── Metal-native LLM inference plane
├── capsule and identity control plane
├── isolated Linux execution provider
└── content-addressed suspension store
```

The model runs on macOS through a Metal-native engine. Typed plans cross a restricted control channel to one isolated Linux environment per active agent. The control plane authorizes capabilities and records observable transitions. The suspension store atomically seals content-addressed workspace blocks, durable state, receipts, signatures, and lineage.

## Product contract

1. Reach semantic quiescence with no uncertain external operations.
2. Seal identity, objectives, workspace, capabilities, and evidence into a signed capsule.
3. Destroy the active runtime and release its compute resources.
4. Transfer the capsule to a compatible provider.
5. Reconnect through `ssh agent-id@runtime-network`.
6. Verify lineage, acquire an exclusive wake lease, and materialize a fresh runtime.
7. Restore the declared checkpoint and continue unfinished work.
8. Collapse back into signed storage after inactivity.

Across every transition, authority may be preserved or reduced, but it must never silently increase.

## Build sequence

| Phase | Scope | Pass condition |
| --- | --- | --- |
| Capsule core | Content-addressed storage, atomic sealing, identity, lineage, receipts, signatures | Restored workspace matches its recorded root hash |
| Isolated execution | Typed operations, mount policy, limits, output capture, filesystem deltas | Observed transition produces an independently verifiable receipt |
| Suspension lifecycle | Quiescence, effect reconciliation, destruction, warm/cold restoration | Pending task continues after the original runtime is destroyed |
| Agent-addressed SSH | Stable identity, resolver, wake leases, anti-rollback, idle collapse | SSH materializes the agent and the runtime disappears after disconnect |

## Run the founder brief

The repository is a static site with a small Python development server.

```bash
python3 server.py
```

Open `http://localhost:3000`.

## Canonical claim

> We built a storage-rooted runtime for persistent AI agents. An agent can suspend into a portable, proof-carrying capsule, release its active machine, wake through the same SSH identity on compatible compute, retain its authorized capabilities and unfinished work, and return to storage when idle. Exact restoration is used where environments are compatible; heterogeneous transitions use explicitly labeled semantic restoration.

## License

Proprietary — all rights reserved.
