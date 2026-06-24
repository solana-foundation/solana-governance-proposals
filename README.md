# Solana Governance Proposals (SGPs)

This repository hosts **Solana Governance Proposals (SGPs)** — documents
proposed by Solana validators for a stake-weighted, on-chain vote using the
[`svmgov`](https://github.com/solana-foundation/solana-governance) program. For
the on-chain mechanics, see
[docs.governance.solana.com](https://docs.governance.solana.com/).

An SGP captures a **stake-weighted directional decision**. It records what the
community wants. It is not strictly focused on the technical detail of how to
build the feature, although SGPs should be feasible in order to be voted on.

## SGP or SIMD?

SGPs and [Solana Improvement Documents (SIMDs)](https://github.com/solana-foundation/solana-improvement-documents)
answer different questions:

| | **SGP** (this repo) | **SIMD** |
|---|---|---|
| **Question it answers** | *Should we do this?* | *How exactly do we do this?* |
| **Altitude** | High-level, directional | Detailed protocol specification |
| **Decided by** | Stake-weighted on-chain vote | Technical review by core developers |
| **Maturity required** | A clear idea worth a community signal | A complete, implementable design |

**Use an SGP when core developers need a signal from stakeholders.**

> **Example — Alpenglow.** Alpenglow, a change to Solana's consensus protocol,
> was taken to a vote as a SIMD. At the time of that vote it was not yet at
> enough technical detail to be *approved* as a SIMD, but core developers still
> needed a directional signal from the community on whether to pursue the
> direction at all. That is exactly what an SGP is for: an SGP could have
> captured the "yes, pursue this" signal first, with the detailed SIMD(s)
> following once the design matured.

A "yes" on an SGP is a mandate to proceed. The implementation work that follows
is normally specified in one or more SIMDs.

## SGP: A signaling vote

The SGP process is a **signaling vote**, and it is **only required when 15% of
stake supports holding one**. By default, decision making rests with the core
developers and the SIMD process. An SGP does not block the SIMD process as a
mandatory step. SGPs **interrupt** a potential SIMD only when the validator set
or stakers demonstrate enough interest to demand a say.

In practice this means:

- If core developers propose a SIMD and **fewer than 15% of stake** signals
  support for a vote, there is **no SGP** — the SIMD process proceeds as normal.
- If **15% of stake or more** supports holding a vote, the SGP process is
  triggered and the decision is put to a stake-weighted vote.

The 15% threshold ensures the network only votes on topics with genuine
interest from the validator set or stakers, and avoids forcing votes on matters
the community has not signaled it wants to weigh in on.

## How an SGP works

Every SGP has **two parts**:

1. **The document** — a markdown file in this repo, opened as a pull request
   (full text, rationale, the exact question being voted on). This is what
   validators and delegators read.
2. **The on-chain proposal** — a `Proposal` account created with `svmgov`,
   whose `description` field links back to the document in this repo at a
   **specific commit**. Support and votes are recorded on-chain.

The on-chain program records the tally; this README defines the **policy** —
what is votable, the thresholds, and what an outcome means.

## What is votable

An SGP is appropriate when **all** of these hold:

- The decision is directional in nature.
- The decision has long term on chain economic impact.
- It benefits from a stake-weighted signal from validators and delegators.

If your idea is already a complete, implementable protocol change, write a SIMD.
If it is a direction that core developers need a mandate on, write an SGP.
Economic changes that need input from the community should be an SGP.

## The proposal document

Copy [`XXXX-sgp-template.md`](./XXXX-sgp-template.md) to
`proposals/XXXX-my-title.md` and open a pull request. Each SGP begins with a
metadata header:

```yaml
---
sgp: <number, assigned in review>
title: <concise descriptive title>
authors: <name(s) and contact>
status: Draft
created: <YYYY-MM-DD>
supersedes: <SGP number, if any>
---
```

and contains, at minimum: a **Summary**, **Motivation**, the **Proposal**
itself, **Rationale**, **Alternatives Considered**, **Impact**, **Relationship
to SIMDs** (what technical work a "yes" would trigger), and the exact **Vote**
question with its options. See the template for the full structure.

## Lifecycle

```
Idea → Draft → Support → Voting ─┬─→ Accepted → Implemented → Activated
                                 └─→ Rejected
```

| State | What it means |
|---|---|
| **Idea** | Vetted in this repo's **Discussions**. Not yet a pull request. |
| **Draft** | A markdown file in an open PR. Text is still being refined. |
| **Support** | Document frozen at a commit SHA; an on-chain `Proposal` exists. Gathering stake support. |
| **Voting** | Support threshold reached. A stake-weighted vote is open. |
| **Accepted** | The vote reached the approval threshold. The direction is mandated. |
| **Rejected** | The vote closed without reaching the approval threshold. |
| **Implemented** | The accepted direction has been carried out (typically via one or more SIMDs and client releases). |
| **Activated** | The change is live on mainnet. |

Side states:

| State | What it means |
|---|---|
| **Withdrawn** | The author closed the SGP before the vote. |
| **Expired** | The Support stage ended without reaching the support threshold. |

## Timeline

Once an SGP is taken on-chain, it follows a fixed schedule measured in epochs.
A Solana epoch is approximately two days.

| Phase | Duration | What happens |
|---|---|---|
| **Support** | Until the threshold is met | Validators signal support. The SGP advances once **15% of active stake** supports it; otherwise it **Expires**. |
| **Discussion** | **7 epochs** | The proposal is locked for debate. The community reviews and discusses; no votes are cast yet. |
| **NCN snapshot** | **1 epoch** | The Node Consensus Network (NCN) captures the stake state that determines voting weights for the vote. |
| **Voting** | **3 epochs** | Stake-weighted voting is open. At the end, the SGP is **Accepted** or **Rejected**. |

After the support threshold is reached, the on-chain process runs for a fixed
**11 epochs** (7 + 1 + 3) before the outcome is final.

## Voting policy

| Parameter | Value |
|---|---|
| **Minimum to submit** | A validator vote account with at least **100,000 SOL** staked |
| **Support to trigger a vote** | **15% of active stake** must signal support to move from `Support` to `Voting` |
| **Quorum** | **None** — there is no minimum turnout |
| **Approval threshold** | **Supermajority** — **`For` ≥ two-thirds (66.67%) of `For` + `Against` stake**. `Abstain` is not counted. |
| **Voting period** | **3 epochs** |

The threshold is measured over decisive votes only: `Abstain` stake is excluded
from the denominator. A vote that does not reach the two-thirds supermajority
within the voting period is **Rejected**.

## Vote integrity

Validators commit stake against the on-chain link, so a frozen SGP **must be
immutable**. SGPs are taken on-chain pinned to a **specific commit SHA** — e.g.
`https://github.com/solana-foundation/solana-governance-proposals/blob/<commit-sha>/proposals/sgp-0042-title.md` —
never a branch or PR. A frozen SGP is never edited; corrections require a new
SGP that supersedes it.

## Submitting an SGP

1. **Discuss** your idea in this repo's **Discussions** before writing a formal SGP.
2. **Confirm** it needs a vote and isn't better served by a SIMD (see
   [SGP or SIMD?](#sgp-or-simd)).
3. **Write** it: copy [`XXXX-sgp-template.md`](./XXXX-sgp-template.md) to
   `proposals/sgp-XXXX-my-title.md` and open a PR. Reviewers assign the number.
4. **Take it on-chain** with `svmgov`, linking to the frozen commit SHA, once
   the document is ready to gather support.

### Requirements to take an SGP on-chain

- A Solana validator vote account with at least **100,000 SOL** staked
- The `svmgov` CLI configured for the target network
- An SGP pull request, frozen at a specific commit SHA
