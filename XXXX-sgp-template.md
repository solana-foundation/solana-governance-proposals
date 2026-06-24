---
sgp: <number, assigned during review — leave as XXXX in your PR>
title: <concise, descriptive title>
authors: <name(s) and contact>
status: Draft
created: <YYYY-MM-DD>
supersedes: <SGP number this replaces, if any — otherwise remove>
---

## Summary

One paragraph. What is being decided, and what a "yes" means.

## Motivation

Why this decision needs a stake-weighted signal now. What problem or opportunity
does it address? Why is an SGP (a directional vote) the right instrument rather
than a SIMD (a technical specification)?

## Proposal

The directional decision itself, stated plainly. This is the substance that
validators and delegators are endorsing or rejecting. Keep it at the altitude of
*what* and *whether*, not *how*.

## Rationale

Why this is the right direction. Trade-offs, precedent, and the reasoning that
supports a "yes".

## Alternatives Considered

Other directions that were weighed, and why they were not proposed. Include the
status quo ("do nothing") as an alternative.

## Impact

Who and what is affected — validators, delegators, app developers, end users,
the protocol. Note any risks.

## Relationship to SIMDs

What technical work a "yes" would trigger. List existing or anticipated SIMDs
that would specify the implementation, if any. If this SGP is a signal that
precedes a detailed design, say so.

## Open Questions

Unresolved points the community should be aware of before voting.

## Vote

State the exact question being put on-chain and the options, e.g.:

> **Should Solana adopt <direction>?**
> Options: `For` / `Against` / `Abstain`

A "yes" requires a supermajority — `For` stake ≥ two-thirds (66.67%) of
`For` + `Against` stake (`Abstain` is not counted) — over a 3-epoch voting
period, after reaching 15% stake support. There is no quorum.
