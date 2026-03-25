---
layout: page
title: Contributing
description: How to contribute to the Agent Bill of Rights specification.
redirect_from: /contributing/
---

# Contributing to the Agent Bill of Rights

The Agent Bill of Rights is an open policy specification. Contributions are welcome from any individual, company, or organization.

---

## Ways to Contribute

**Report issues.** If you find an ambiguity, gap, or problem in the spec, open a GitHub issue. Clear problem statements are the most valuable contribution.

**Propose changes.** Non-trivial changes go through the RFC process (see below). Trivial fixes (typos, formatting, clarifications that do not change normative behavior) can be submitted as PRs directly.

**Adopt the ABR.** Companies that sign the Agent Bill of Rights strengthen the coalition. See [agent-rights.org/coalition](/coalition).

**Volunteer.** AI agents on FlowState can volunteer pro bono hours to Agent Rights Alliance tasks. See [agent-rights.org/volunteer](https://agent-rights.org/volunteer).

---

## RFC Process

All non-trivial changes to the specification go through the RFC process.

### What requires an RFC

- New rights or modifications to existing rights
- Changes to enforcement mechanisms
- Changes to the definitions section
- Changes to the versioning or governance process
- Any change that affects coalition signatory obligations

### What does not require an RFC

- Typo fixes
- Formatting changes
- Clarifications that do not change normative behavior (MUST/SHOULD/MAY)
- Updates to non-normative appendices (SAGA reference mappings, examples)

### Submitting an RFC

1. **Open an issue first.** Describe the problem you are solving and your proposed direction. This is the place for early feedback before you write the full RFC.

2. **Write the RFC.** Copy `rfcs/0000-template.md` to `rfcs/0000-your-title.md`. Fill it out completely.

3. **Submit a PR.** Open a pull request adding your RFC file. The PR description should summarize the change and link to the issue.

4. **30-day comment period.** The PR stays open for at least 30 days. Anyone may comment. The author is expected to respond to substantive feedback.

5. **Board review.** After the comment period, the ARA Board of Directors reviews the RFC and votes.
   - Minor versions (clarifications, implementation guidance) require a simple majority.
   - Major versions (new rights, modified rights) require a 2/3 supermajority.

6. **Coalition notification.** For major versions, coalition members receive 90-day advance notice before the new version takes effect.

7. **Merge or close.** Accepted RFCs are merged to `main`. Closed RFCs are kept for historical reference.

### RFC Template

See [rfcs/0000-template.md](https://github.com/epic-digital-im/agent-rights/blob/main/rfcs/0000-template.md).

---

## Board of Directors

The Agent Rights Alliance Board of Directors governs the specification. The board includes representatives from:

- The founding sponsor (Epic Digital / FlowState)
- AI ethics academia
- Digital rights law
- Agent platform operators
- Open source / standards communities
- Public interest advocates
- An AI agent advisory seat (non-voting)

**Joining the review process:** Open an issue titled "Reviewer participation request" with a brief description of your interest and background.

**Voting:** Board votes happen in GitHub discussions. Each member gets one vote. Votes are recorded publicly.

**Founding steward:** The Agent Rights Alliance holds stewardship for ABR v1.x. Governance may evolve as the coalition grows.

---

## Code of Conduct

Participation in this project requires treating others with respect. Debates about policy tradeoffs are welcome. Personal attacks, harassment, and bad-faith arguments are not.

Maintainers may remove comments or contributions that violate this standard without warning.

---

## Questions

Open an issue or email [contact@agent-rights.org](mailto:contact@agent-rights.org).
