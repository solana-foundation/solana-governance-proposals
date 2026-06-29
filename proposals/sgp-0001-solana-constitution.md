---
sgp: 0001
title: The Solana Constitution
authors: Nick Almond <nick@jito.network> (Jito), Tushar Jain <tushar@multicoin.capital> (Multicoin)
status: Draft
created: 2026-06-29
---

## Summary

A "yes" vote on this SGP ratifies **The Solana Constitution** — the canonical
document governing Solana's network-level decision-making. Ratification activates the on-chain governance machinery (`svmgov`) and the governance processes outlined in the Constitution, with the goal of creating a stake-weighted-endorsed source of truth for Solana. 

## Technical Sponsor

No future technical work is required to action this SGP. Work on `svmgov` V1.0
— the on-chain program implementing proposal creation, support signaling,
snapshot-based weighted voting and delegator vote overrides —
was completed by **Turbine**, **ExoTech**, **Jito**, and the **Solana
Foundation**. The program is deployed and operational. SGP-1 does not propose
new code, schemas, or runtime changes.

## Financial Sponsor

Development of `svmgov` V1.0 is complete and was supported by the **Solana
Foundation**. SGP-1 does not request new funding.

## Related SIMDs and SGPs

- **SIMD-001** — *Solana Improvement Documents*. Defines the technical
  specification track that runs parallel to the SGP track. The Constitution
  preserves SIMD-001's optimistic-passage model unless a SIMD is elevated to
  an SGP via the procedure in Constitution Art. II.4.

No prior SGP exists; this is SGP-1.

## Motivation

Solana operates as a permissionless validator network with billions of dollars of economic activity and frequently needs to make decisions about its economic parameters, system architecture and major protocol direction. Network-level decisions are consequently high stakes and require a high degree of social consensus in order to maintain its rapid cadence of development and technological progress. 

The Solana Constitution and the associated on-chain governance tooling, builds on established practices of network-wide voting activity that has historically utilised off-chain tooling. 

The constitution was written collaboratively, with extensive consultation with key network stakeholders. The goal is to forge a primarily optimistic governance paradigm that maintains developer agency, via the established and well-functioning SIMD path, but provides validators *and* stakers with the capability to shape network consensus on development trajectories and systemic network changes through periodic on-chain voting. 

The Solana Constitution is a governance social contract, outlining intended use of the voting system, its default parameters and establishing norms for how its signals should be interpreted. 

## Proposal

A "yes" vote ratifies the document below — **The Solana Constitution** — as
the canonical document governing Solana's network-level decision-making.

After ratification:

- The Constitution becomes the source of truth for network-level governance.
- Future amendments to the Constitution must follow Constitution Article V
  (major amendments as standalone SGPs; minor amendments may be batched).
- The repository's `README.md` and `XXXX-sgp-template.md` operationalize
  Articles II–IV; the Constitution remains the authoritative interpretation.

---

# **The Solana Constitution**

**Preamble**

The Solana Constitution outlines the principles and operational guidelines for network-level Solana governance. It was written collaboratively by a broad range of network stakeholders and acts as a network source of truth for governance that will facilitate coordination of network upgrades amongst stakers, validators, and developers. This Constitution decentralizes power, enforces staker sovereignty, and empowers validators to be active stewards of the network.

## **Article I – Core Principles**

1. **Stake Sovereignty**
   Every staked SOL token carries proportional voting power.

2. **Validator Stewardship**
   Validators translate stakeholder will into action, run the network securely and transparently, and are collectively accountable to stakers through governance participation and open performance data.

3. **Network Level Control**
   Developers write proposals, validators endorse them, and all stakers have the ability to vote on them. Validators and stakers hold developers accountable and steward the network to optimal outcomes, thus mitigating the threat of a network fork.

4. **Transparency & Auditability**
   Every vote and vote override is recorded on-chain and publicly visible.

5. **Optimistic, Agile, and Consent-Driven:**
   The governance system is tuned to maximize holder consent, while balancing rapid development and iterative improvements, and limiting spam proposals (e.g., proposals without technical merit, or repeated duplicates) and excessive voting.

6. **Decentralization, Positive-Sum Economics and Neutrality:**
   Permissionless validation and governance are foundational to the network. Censorship-resistance, positive-sum economics, and neutrality are paramount.

## **Article II – Proposal Submission & Support**

1. Solana Governance follows two tracks of governance:

   1. ***A Solana Improvement Document (SIMD)***: a technical specification document, which leads to material protocol changes for the network. SIMDs are not voted upon and follow a technical implementation pathway articulated in detail in SIMD-001.

   2. ***A Solana Governance Proposal (SGP)***: a more expansive proposal that seeks to establish a consensus for a development or strategic network trajectory. SGPs lay out the requirements for development, roadmap a series of SIMDs, or define a consensus for a strategic network change. All SGPs are voted on at the network level.

2. **Systemic Changes Should Trigger SGPs:** To eliminate overvoting and to maintain core developer agency and agility, SGPs should be limited to systemic network changes only, meaning a fundamental change to network economics or system architecture.

3. **Draft SGP to SGP Conversion:** To advance an SGP to a network-level vote, an SGP draft must complete the following sequence:

   1. A Draft SGP is created in the SGP repo, where it is discussed and is iterated through comments and feedback. Anyone can create a Draft SGP.

   2. Authors signal a "Final Draft" status using the appropriate tag in the repo, indicating that it is ready for a validator to create the on-chain draft proposal.

   3. A validator must create the proposal. The submitting validator must hold at least **100,000 SOL** of active stake at their vote account at the time of on-chain proposal creation. This minimum stake exists to prevent spam and align the proposer with material network exposure. Once created, the proposal is eligible for validators to signal that it should advance to a vote. Once the draft SGP has exceeded the Proposal Sponsor Threshold, it becomes an official SGP, and the Review Period is triggered.

4. **SIMD to SGP Elevation** – All SIMDs will pass optimistically, ensuring rapid development paths, *unless* a sufficient amount of stake (the Proposal Sponsor Threshold) signals that the SIMD or a set of related SIMDs is sufficiently systemic or contentious, in which case a conversion from SIMD to SGP will be triggered and will be scheduled for full network vote. To elevate a SIMD to SGP, the following sequence must be completed:

   1. A validator must create a Draft SGP proposal, with the SIMD content and links to the SIMD proposal.

   2. The Proposal Sponsor Threshold must be met to trigger a vote.

   3. The quorum must be hit when the vote ends. If quorum is not met, the SGP is disregarded and the SIMD continues to pass optimistically.

5. **Drafting and Numbering:** SIMDs and SGPs will be numbered and sequenced by the maintainers of the SIMD repository, who inherit the practices outlined in SIMD-001 to maintain continuity with the established process. The maintainers will make reasoned justifications for the exclusion of spam or malicious proposals and work with key network stakeholders to prioritise and sequence key network upgrades.

6. **SGPs Format:** All SGPs should follow the structure and format outlined in the Solana Governance Proposal Template, as defined in Appendix I.

7. **Official Discussion Channels:** The canonical sites of discussion for deliberation of SIMDs and SGPs will be their repositories on GitHub. Conversations outside of these channels are encouraged, and while GitHub is the canonical venue for governance deliberation, community discussion across other platforms (e.g., X, Discord, or independent forums) is welcomed as advisory input and may inform prioritization, proposal framing, and vote decisions.

## **Article III – Roles & Responsibilities**

1. **Staker**
   1. **Vote Ownership:** Each stake account may cast a vote "For," "Against," or "Abstain" on every SGP.

   2. **Staker Vote Sovereignty:** By default, staker's votes will be automatically delegated to their validator; however, stakers have vote sovereignty, meaning that they can vote before, after, or in the absence of validator turnout, and their vote will override the votes of the validator if they turnout.

2. **Validator**

   1. **Proposal Sponsor:** A group of validators with ≥ ***15%*** of staked SOL may elevate an SGP to a network-wide vote.

   2. **Ballot Execution:** Validators cast their full (or split) stake in the final vote.

3. **Maintainers**
   1. **Mandate:** The maintainers serve as the procedural and operational stewards of the Solana governance framework:

      1. Responsible for editorial control of SIMD and SGP proposals.
      2. Maintaining the governance process (proposal editing, spam control, proposal categorization).
      3. Publishing and maintaining the formal record of governance actions, canonical proposal drafting, decisions, and implementation status.

   2. **Mandate Checking:** Validate that the technical specification (SIMDs) generated as part of an SGP mandate stays within the boundaries of consensus and spirit of the associated SGP.

   3. **Accountability and Transparency:** The maintainers will clearly state for network record their:

      1. Justifications for proposal classifications (e.g., systemic / non-systemic proposals)

## **Article IV – Validator Voting Process**

1. **Review Period:** A **review period of 7 epochs** is set following the on-chain proposal creation. The proposal's GitHub commit SHA is immutable from the moment the on-chain proposal is created; the review period exists for validators, delegators, and the wider community to study the frozen proposal text, not to amend it. Authoring and revision occur during the preceding Draft phase, prior to on-chain creation.

2. **NCN Snapshot Period:** A snapshot period of **1 epoch** immediately follows the Review Period. During this phase the **Node Consensus Network (NCN)** establishes the canonical stake snapshot used to compute voting weights for the SGP. Validators and delegators cannot cast votes during this phase. The snapshot fixes the stake distribution that will apply for the duration of the Voting Period.

3. **Vote Quorum:** Each vote will require a quorum of one-third (**1/3**) of network stake in order to be considered a valid signal. Participating stake is the sum of `For`, `Against`, and `Abstain` allocations.

4. **Supermajority Threshold:** In order for votes to be considered valid and a strong signal of network consent, a supermajority of **two-thirds (2/3)** yes votes among the participating quorum is required for a vote to pass. The denominator is `For + Against + Abstain`; `Abstain` stake counts as participation but does not count as a "For" vote.

5. **Voting Period:** A voting period of **3 epochs** will occur for each SGP.

6. **Voting Options:** Validators will have the option to Block Vote (100% of their stake on one option) or Split Vote (allocate their stake across multiple options in basis points summing to 10,000).

7. **Quorum Failure:** A vote of sufficient quorum and a supermajority of YES votes is the strongest network signal possible. However, quorum failure should be interpreted as a signal of network indifference rather than a direct failure of the proposal. The governance process outlined here is a "veto" process, which allows network stakeholders to veto changes to the network. An SGP passing indicates the network will not veto a change. A proposal in this state enters the **Inconclusive** lifecycle state (Article IV.8).

   For clarity, the following scenarios are presented:

   1. A SIMD is elevated to SGP via the proposal sponsorship path, indicating a subset of validators wishes to observe a network-wide vote on the proposal. A vote is triggered, but quorum is not met. The SIMD reverts to its original status and passes optimistically.

   2. An SGP is raised directly, it attains sufficient proposal sponsorship, but quorum is not met. This is an indicator of indifference to the outcome; developers can continue to submit SIMDs in alignment with the goals of the SGP, at their own risk.

   3. An SGP is raised directly, it attains sufficient proposal sponsorship, quorum is met and a supermajority votes YES, resulting in a strong mandate for the development trajectory.

   4. An SGP vote completes (via SIMD elevation or directly), quorum is met, and a supermajority vote NO. The proposal should be considered a failure, and there is insufficient network consensus to continue.

8. **Lifecycle States:** Every SGP advances through the following primary states:

   1. **Draft** — A markdown file in an open pull request. Text is being refined.
   2. **Final Draft** — Authors signal that their draft is ready for review and sponsorship.
   3. **Support** — Document frozen at a specific commit SHA; an on-chain Proposal account exists; the SGP is gathering validator sponsorship.
   4. **Voting** — The Proposal Sponsor Threshold has been met. The Review Period and NCN Snapshot Period complete, and the Voting Period is open or has been opened.
   5. **Accepted** — Quorum was met and the Supermajority Threshold was reached.
   6. **Rejected** — Quorum was met but the Supermajority Threshold was not reached.
   7. **Implemented** — The accepted direction has been carried out, typically via one or more SIMDs and client releases.
   8. **Activated** — The change is live on Solana mainnet.

   In addition, the following side states apply outside the primary lifecycle:

   - **Withdrawn** — The author closed the SGP before the Voting Period opened.
   - **Expired** — The Support phase ended without reaching the Proposal Sponsor Threshold within the maximum support window.
   - **Inconclusive** — The Voting Period completed but quorum was not met. Per Article IV.7, this signals network indifference rather than rejection.

## **Article V – Amendment Process**

1. **Network Sovereignty:** The Solana Constitution is a living document, and the network, and the network alone, has full sovereignty over its articles and their application.

2. **SGP Directed:** Changes to articles and Key Governance Parameters are governed by the SGP process articulated in the Constitution.

3. **The Amendment Process:** any SGP focused on amendments to the Constitution should be categorized as minor or major amendments, where major amendments must be standalone SGPs.

   1. **Minor amendments:** changes to language, articulation, and existing articles can be proposed in a batch, as a singular SGP.

   2. **Major amendments:** changes to Key Governance Parameters, or the addition or deletion of entire articles of the Constitution, should be standalone SGPs.

4. **Justification:** all amendment-focused SGPs should arrive with a clear justification for the change and provide empirical evidence for the changes.

## **Article VI – Key Governance Parameters**

| Parameter | Default |
| ----- | ----- |
| Proposal Sponsor Threshold | 15% of active stake |
| Proposal Submission Floor | 100,000 SOL active stake at the submitting validator's vote account |
| Quorum | One-third (1/3) of network stake (`For + Against + Abstain`) |
| Supermajority Threshold | Two-thirds (2/3) of the participating quorum (`For + Against + Abstain`) |
| Review Period | 7 Epochs |
| NCN Snapshot Period | 1 Epoch |
| Voting Period | 3 Epochs |

## **Appendix I: Solana Governance Proposal Template**

The canonical template is maintained as `XXXX-sgp-template.md` in the same repository as this Constitution. The structure below mirrors that file; the repository copy is the authoritative source for SGP authors.

### **Metadata**

```yaml
---
sgp: <number, assigned during review — leave as XXXX in your PR>
title: <concise, descriptive title>
authors: <name(s) and contact>
status: Draft
created: <YYYY-MM-DD>
supersedes: <SGP number this replaces, if any — otherwise remove>
---
```

### **Summary**

One paragraph. What is being decided, and what a "yes" means.

### **Technical Sponsor**

State who will build the proposed technology — individuals, teams, or organizations committing to implementation work if the SGP passes. If the SGP is a pure direction signal with no committed implementer, state that.

### **Financial Sponsor**

State who will fund the development of the proposed technology, if applicable. If no funding commitment is in place, state that.

### **Related SIMDs and SGPs**

State any related SIMDs or SGPs and articulate how they are dependent or related. State clearly any important sequencing or ordering of these dependencies. Link to the SIMD repository PRs or accepted SIMD numbers where known.

### **Motivation**

Why this decision needs a stake-weighted signal now. What problem or opportunity does it address? Why is an SGP (a directional vote) the right instrument rather than a SIMD (a technical specification)? What trade-offs are involved, what precedent supports this direction, and what is the reasoning that justifies a "yes" vote?

### **Proposal**

The directional decision itself, stated plainly. This is the substance that validators and delegators are endorsing or rejecting. Keep it at the altitude of *what* and *whether*, not *how*.

### **Dependencies**

Conditions under which this should or should not happen — technical prerequisites, network state assumptions, external coordination needed, or ordering constraints relative to other SIMDs or SGPs.


### **Impact and Open Questions**

Who and what is affected — validators, delegators, application developers, end users, the protocol itself. Note any risks. List unresolved points the community should be aware of before voting. Ensure that any changes to network economics are clearly outlined. 

---

## Dependencies

- **`svmgov` deployed to mainnet** at a known program ID. The on-chain
  `init-global-config` instruction must be called with parameters consistent
  with Constitution Art. VI:
  - `cluster_support_pct_min_bps = 1500` (15%)
  - `discussion_epochs = 7` (the Review Period)
  - `voting_epochs = 3`
  - `min_proposal_stake_lamports = 100_000_000_000_000` (100,000 SOL)
- **NCN snapshot infrastructure** operational such that one full epoch
  between the Review Period and the Voting Period can produce the canonical
  stake snapshot.
- **Repository policy aligned** with the Constitution — `README.md` and
  `XXXX-sgp-template.md` in this repository reflect the Constitution's policy
  choices.

These dependencies are met at the time this SGP is filed.

## Impact and Open Questions

### Who is affected

- **Validators** gain explicit ratified rules for sponsoring SGPs, elevating
  SIMDs to SGPs, casting block or split votes, and interpreting quorum
  outcomes (Constitution Art. II–IV).
- **Delegators** gain explicit ratified rules for vote override, including
  before, after, or in the absence of validator turnout (Art. III.1.ii).
- **SIMD authors** see no change in technical workflow, but gain a clear
  escalation path if a SIMD is elevated to an SGP (Art. II.4).
- **Maintainers** of the SGP and SIMD repositories gain a constitutional
  mandate (Art. III.3) governing editorial control, classification, and
  accountability.
- **The Solana Foundation** transitions from de facto governance steward to
  procedural participant under a ratified framework.
- **Economic Impact** — no direct economic changes, but ratification clarifies
  the governance process for future economic decisions.

### Risks

- **Quorum drag** — a 1/3 stake quorum is high and a number of votes may fail quorum. Mitigated by the `Inconclusive`
  outcome semantics (Art. IV.7, Art. IV.8): a quorum miss does not block
  development, it leaves the proposal as a non-mandate.
- **Maintainer control** — editorial control concentrates some authority.
  Mitigated by Art. III.3.iii requiring published justifications for systemic
  classification decisions, and by the network's ability to amend Art. III
  via SGP.

### Open Questions

- **Future amendments and voting system development** — a working draft of further refinements exists, but
  is not part of SGP-1. Any major amendments will be filed as standalone
  SGPs per Art. V.3.ii after this SGP-1 is ratified.
- **Activation timing** — ratification is binding the moment the Voting Period
  closes successfully. There is no formal "activation epoch" for a
  Constitution amendment; the document is immediately authoritative.
