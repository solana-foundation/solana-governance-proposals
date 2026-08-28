---
sgp: 0003
title: Resource and Inclusion Fee
authors: cavey
status: Rejected
created: 2026-08-03
supersedes:
---

## Summary

This SGP asks validators and delegators to endorse restructuring Solana's base
transaction fee into a fixed **base inclusion fee** paid to the block leader and
a separate **resource fee** that scales with requested transaction cost and is
**100% burned**. A "yes" is a mandate to pursue that fee model; the detailed
mechanism is specified in [SIMD-0553][simd-0553].

## Motivation

Today every transaction pays a flat **5,000-lamport per-signature** base fee
(half burned, half to the leader), regardless of how much compute, write locks,
or loaded data it requests. That leaves two problems:

1. **Burn is negligible relative to inflation.** At current throughput, signature
   fee burn is on the order of ~648 SOL/day — far below daily inflation
   (~60,000 SOL/day).
2. **Resources are mispriced.** Light transactions and heavy ones pay the same
   base charge, so compute-heavy activity is underpriced at the base layer while
   efficient, low-resource traffic gets no break.

This is a directional, network-level economics question — *should* Solana price
inclusion and resources this way? The technical design lives in SIMD-0553; this
vote is the stake-weighted mandate to proceed with that direction.

## Proposal

Endorse the following fee model for on-chain transactions:

- Keep a static **base inclusion fee** of **2,500 lamports per transaction**,
  paid **100% to the block leader**.
- Introduce a **resource fee** computed from **requested cost units**, burned
  **100%**, with a staged rate ramp (feature-gated) up to a terminal rate of
  **1/2 lamport per requested cost unit**.
- Leave **priority fees** unchanged (**100% to the leader**, per SIMD-0096).

A "yes" means the network supports activating this direction via the SIMD /
feature-gate process. It does not itself activate any feature gate.

## Rationale

- **Price what the transaction costs.** Requested cost units already drive block
  packing; charging a burned resource fee on that quantity aligns base fees with
  the work every node must absorb.
- **Preserve leader inclusion incentives.** A nonzero inclusion fee remains so
  leaders are paid even when priority fees are zero. Resource fee is burned
  instead of given to validators or stakers to not disrupt current incentive
  structure and market structure, i.e. do not incentivize inefficient smart
  contracts, or swaps over quote updates.
- **Burn scales with demand.** Resource-heavy activity contributes more SOL burn;
  light, efficient transactions can pay less than under today's flat base fee.
- **Stage the rate.** A feature-gated ramp (1/10 → 1/4 → 1/2) lets applications
  adapt before the terminal rate, while keeping validator priority-fee economics
  intact.
- **Charge requested, not consumed.** Same predictability rationale as priority
  fees: fee known before execution, better UX, and an incentive to request
  accurate compute budgets.

## Alternatives Considered

- **Status quo (do nothing).** Leaves resource usage free and keep base-fee burn.
- **Uniform increase to the flat 5,000-lamport fee.** Hits high-volume, low-resource
  senders (e.g. market makers) hardest while still failing to price compute.
- **Split the resource fee 50/50 burn / leader.** Rejected in SIMD-0553: resource
  cost is borne by all replaying nodes, not only the leader; paying the leader a
  share distorts incentives toward inefficient, fee-heavy programs.
- **Dynamic rate controller from utilization.** Reasonable follow-up; out of scope
  for the initial directional decision. SIMD-0553 uses staged static rates.
- **SIMD-0110-style hot-account base fees.** Local and short-timescale; this
  proposal is global and tied to per-transaction requested cost.

## Impact

- **SOL holders.** Empirical estimates in SIMD-0553 (May 2026 network data)
  suggest roughly **~1,500–1,800 / ~3,750–4,500 / ~7,500–9,000 SOL/day** of
  resource-fee burn at the **1/10 / 1/4 / 1/2** rates respectively, replacing
  ~648 SOL/day of flat signature-fee burn at current throughput.
- **Low-resource users.** At the terminal rate, efficient transactions (e.g.
  oracle updates, correctly budgeted votes) can pay **less** than today's
  flat 5,000-lamport base fee.
- **High-compute / loose-budget users.** Zero- and low-priority traffic that
  over-requests compute units will see **much higher** fees until wallets and
  apps tighten Compute Budget limits and programs are optimized.
- **Validators.** Inclusion + priority fee economics stay with the leader;
  resource fee is burned. Pre-Alpenglow vote cost depends on requesting accurate
  vote compute budgets (see SIMD-0553).
- **Wallets / RPCs / apps.** Must estimate `total_fee` under the new model before
  activation; loose default compute limits become expensive.

Risks include a lower lamport floor for minimal spam transactions at early gate
rates, and activation friction for apps that still omit Compute Budget
instructions.

## Relationship to SIMDs

A "yes" endorses implementing and activating the design in:

- **[SIMD-0553: Resource and Inclusion Fee][simd-0553]** — primary specification
  (base inclusion fee, resource fee formula, staged feature gates, RPC/client
  guidance).

Related context:

- **[Discussion #547][discussion-547]** — originating design discussion.
- **[SIMD-0096][simd-0096]** — priority fees remain 100% to the leader.
- Companion tokenomics work (e.g. disinflation SGPs / SIMD-0550) is separate; this
  SGP is only about the fee model.

## Open Questions

- Exact mainnet activation timing for each feature gate (1/10 → 1/4 → 1/2), and
  how long to observe each stage.
- Whether a later SIMD should reprice signature cost in the cost model for
  multi-signer / precompile-heavy transactions (called out as follow-up in
  SIMD-0553).
- Ecosystem readiness: how quickly wallets, SDKs, and high-volume apps adopt
  accurate Compute Budget requests before the terminal rate.

## Vote

> **Should Solana adopt a base inclusion fee plus a burned resource fee that
> scales with requested cost units, as specified in SIMD-0553?**
>
> Options: `For` / `Against` / `Abstain`

A "yes" requires a supermajority — `For` stake ≥ two-thirds (66.67%) of
`For` + `Against` stake (`Abstain` is not counted) — over a 3-epoch voting
period, after reaching 15% stake support. There is no quorum.

[simd-0553]: https://github.com/solana-foundation/solana-improvement-documents/pull/553
[discussion-547]: https://github.com/solana-foundation/solana-improvement-documents/discussions/547
[simd-0096]: https://github.com/solana-foundation/solana-improvement-documents/blob/main/proposals/0096-priority-fee-distribution.md
