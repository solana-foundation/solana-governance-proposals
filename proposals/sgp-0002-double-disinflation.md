---
sgp: XXXX
title: Double Disinflation Rate
authors: Lostin & 0xIchigo (Helius)
status: Draft
created: 2026-07-03
---

## Summary

Reduce the inflation schedule by increasing the disinflation rate from the
current -15% rate to -30%.

## Technical Sponsor

Not required for this SGP.

The technical change is intentionally minimal and should be implemented
through the normal Solana client development process. The relevant client
teams should ensure the feature gate, conformance tests, and activation
behavior are implemented consistently across validator clients.

## Financial Sponsor

Not required for this SGP.

No separate funding request is proposed. The change is small in
implementation scope and can be handled through existing protocol
development processes.

## Related SIMDs and SGPs

[SIMD-0550 Double Disinflation Rate](https://github.com/solana-foundation/solana-improvement-documents/pull/550):
The primary related SIMD. This SGP is intended to express validator and
governance support for SIMD-0550 and its rollout requirements.

[SIMD-0411 Prior Double Disinflation Proposal](https://github.com/solana-foundation/solana-improvement-documents/pull/411):
An earlier version of SIMD-0550 that proposes the same changes.

[SIMD-0228 Market-Based Emission Mechanism](https://github.com/solana-foundation/solana-improvement-documents/pull/228):
Relevant historical context. SIMD-0228 proposed a more complex inflation
mechanism and failed to reach quorum.

## Motivation

While there is a significant appetite to reduce the nominal inflation rate of
SOL, mechanism design has become a point of contention, ultimately leading to
SIMD 228 failing to reach quorum. This SGP represents a simplification of the
idea, delivering predictable inflation reduction by doubling the disinflation
rate.

An SGP is the right instrument because this is first and foremost a governance
question: should the network pursue a faster reduction in SOL inflation?

## Proposal

This proposal asks validators and delegators to endorse doubling Solana's
annual disinflation rate from 15% to 30%. After activation, SOL inflation
should decline toward the 1.5% terminal rate twice as quickly as it does
today.

This proposal preserves the current design of Solana's inflation schedule:

- the terminal inflation rate remains at 1.5%
- the schedule remains deterministic and predictable
- staking rewards continue to use the existing protocol reward mechanism
- commissions, MEV, transaction fees, and block rewards are unchanged

## Dependencies

This SGP depends on SIMD-0550 being accepted and activated through the
normal Solana feature-gate process.

## Impact and Open Questions

Doubling disinflation accelerates the timeline of reaching the terminal
emissions rate from a period of ~5.7 years to ~2.8 years. This would result in
a reduction of approximately ~18.9 million SOL in emissions over the next 6
years, which is ~2.6% lower than the current disinflation schedule. With 41% of
validators already opting for a 0% commission on emissions, this change would
result in little realized reduction in revenue for many validators, with a soft
taper so the remaining 59% do not experience any immediate significant shock to
projected earnings. A more detailed breakdown can be found in the [accompanying
forum post](https://forum.solana.com/t/simd-0550-proposal-to-double-disinflation/4874).

- The realized impact on validator economics depends in part on future staking
  participation and commission trends, which may shift before activation.
