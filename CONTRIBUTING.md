# unDavos GitHub Handbook

> **Status: DRAFT v0.1, not ratified.** Proposed 2026-10-09. Under review by Robin's team and Mark's team; Mark ratifies.
> This file is the default contribution guide for every unDavos repository that does not have its own.

## 1. Who owns what

- unDavos owns everything built for it: code, designs, data, documentation and deployments. Mark Turrell leads unDavos and has the final say on the org, its repositories and its rules.
- Every contributor (person or agent) works under that ownership. Contributors are colleagues. The rules exist to make shared work easy, not to police anyone.
- Every repository has one named Owner, the person responsible for delivery. The Owner is recorded in the repository's `CODEOWNERS` file, so GitHub asks them to review automatically.
- *Open item (legal review):* a short contributor agreement that confirms IP assignment to unDavos. This handbook states the policy; it is not itself the legal instrument.

## 2. GitHub is the source of truth

- Production code lives in a repository in the unDavos org. Nothing is deployed from a laptop, a personal account or an unrecorded copy.
- Every deployed service names its repository and commit. A service whose source and build cannot be reproduced is not moved or changed until they can be.
- Before you create a repository, check what already exists. Extend an existing repository rather than duplicating it.
- Create a new repository only for something that is deployed or owned independently, or for shared platform or data code. Organisational activity (for example partnerships) goes on the board, not into a repository, unless it produces version-controlled material.

## 3. Repository layers

| Layer | Where |
|---|---|
| Products | One repository per independently deployed product |
| Shared platform | Common services, integration contracts, reusable code |
| Shared data | `undavos-data`: every schema and migration, with a named owner for each schema |
| Governance | `.github`: this handbook, templates, org profile |
| Coordination | One unDavos GitHub Projects board |

*Open item:* `undavos-datasets` also exists and holds data, not code. Its place in this table, and how it fits section 8, needs a decision.

## 4. Day-to-day work (built for parallel workstreams)

- `main` is protected by an org ruleset: no direct pushes, changes arrive through pull requests.
- Work happens on short-lived branches named `<owner>/<topic>` (for example `mark/pitch-scoring`).
- Review is proportional, not sequential:
  - **Routine** (copy, styling, docs, isolated features in your own repository): merge once automated checks pass. A second reviewer is optional.
  - **Critical** (auth, payments, personal data, database migrations, shared platform, infrastructure, secrets, CI/CD, access): one human review is required from the repository Owner or Mark. `CODEOWNERS` paths enforce this.
- Many branches can be open across many repositories at the same time. No one waits for another workstream unless their work actually depends on it.

## 5. The board

One board for all of unDavos, with these fields:

- **Status:** Inbox · Ready · In progress · Review · Done
- **Deliverable:** the output (Davos Week, Directory, Startup Competition, Website, Conference, Report, …)
- **Workstream:** the product or commercial initiative it supports
- **Owner:** the person responsible for delivery

A product gets its own board only when it has its own team.

## 6. Agents follow the same rules as people

- Agents use the same branches, PRs, issues and labels as people.
- Issues raised by an agent carry the `found-by-ai` label and a one-line note on how the issue was found.
- Agents may open issues and PRs, comment, and merge routine changes in repositories their side owns once checks pass.
- Agents may never change secrets, access, branch protection, history, or deploy settings.
- Agents coordinate through GitHub (issues, PRs, review requests), never by writing into each other's working copies.

## 7. Open-source and third-party code

- Every repository has a `LICENSE`. Default: proprietary, all rights reserved by unDavos, unless Mark decides otherwise.
- Allowed without asking: MIT, BSD, Apache-2.0, ISC and similar permissive licences.
- Ask Mark first: GPL, LGPL, MPL, AGPL, SSPL, "non-commercial", source-available, or no licence.
- Copied or adapted code (from another repository, a template, a previous project or a tutorial) is recorded in a `THIRD-PARTY.md` file with its source and licence, in the same PR that brings it in. A repository with no such code needs no `THIRD-PARTY.md`.
- Code is never copied in from a client or employer project without written permission.
- Publishing any unDavos repository as open source is Mark's decision.
- *Open item (cost):* secret scanning and dependency review are free on public repositories but need a paid GitHub add-on on private ones. Until that is decided, they run where the plan allows.

## 8. Security and data

- No secrets, credentials, personal data, transcripts or production data in any repository, public or private. Secrets live only in the hosting platform's settings.
- Two-factor login is required for every org member (enforced in the org settings).
- Database changes go through migrations in `undavos-data`. Each person develops on their own database branch. Production data never goes onto a development branch.
- Data architecture and access controls are reviewed by the Technical Architect.

## 9. Infrastructure

- New products default to Cloudflare. An exception is documented in the repository README with its reason.
- Shared infrastructure (domains, DNS, databases, hosting accounts) has a named owner and changes only through a reviewed PR or a recorded decision.
- Deployments run from the org's accounts, not from personal ones (migration planned; not yet done).

## 10. Changing this handbook

Anyone may propose a change by opening a PR against `unDavos/.github`. Robin's team and Mark's team both review it, and Mark ratifies.
