# How we work together

This page is the shared floor for every repository in the [`unDavos`](https://github.com/unDavos) organisation. GitHub shows it in any repo that has no `CONTRIBUTING.md` of its own.

It is for people and for AI agents. Robin, Mark, Stéphanie and every agent that works for one of them use the same simple rules. The base is [GitHub Flow](https://docs.github.com/en/get-started/using-github/github-flow): issue, branch, pull request, review, merge.

**A repo's own `CONTRIBUTING.md` wins.** Read it first. If it says something different (checks to run, who approves, how it deploys), follow the repo. A good example is [elixiroflife](https://github.com/unDavos/elixiroflife/blob/main/CONTRIBUTING.md).

## The 3 rules

1. **If it is not in an issue, it does not exist.** Feedback from Telegram, email, a call or a test goes into an issue, with its files.
2. **Every change goes through a pull request.** No direct push to `main` (or to the branch the repo promotes from, for example `staging`).
3. **Somebody else looks before it merges.** The person or agent who made the change never approves it alone.

The organisation is on the GitHub Free plan, so nothing technical blocks a push to `main`. These rules hold because we keep them.

## Before you start

- Run `git fetch origin` and read the open issues. Old local copies have overwritten newer work before.
- Read the repo's `CONTRIBUTING.md`, `README.md`, and `AGENTS.md` or `CLAUDE.md` if they exist. Agents: they are your instructions for that repo.
- If your local folder has changes you did not make, stop and ask. Do not stash or discard them.
- Start from the latest `origin/main`, never from an old branch.

## Issues are the backlog

- One issue for one thing: one bug, one idea, one piece of feedback.
- Put the files in the issue: screenshots, PDFs, recordings.
- Write where it came from: who, when, where. Example: "Mark, Telegram, 18.11.2026".
- Claim an issue before you start: assign yourself, or comment "Claimed by <name>'s agent on `<branch>`".
- Parked work gets a label, not a close.
- Close an issue only when it is done or you decide not to do it. Write why in a last comment.
- When you tell a person about an issue or pull request, give the title and the full link. Never a bare `#12`.

### Labels

Give each issue one **type** label. Add the others only when true. A repo may use a subset.

| Label | Use it for |
| --- | --- |
| `bug`, `feedback`, `idea`, `content`, `design`, `question`, `documentation` | The type. One per issue. |
| `priority:blocker` | Stops the main thing working. Fix first. |
| `waiting:decision` | Waits on a person to choose. Name them. |
| `waiting:action` | Waits on a person to do something. Name them. |
| `waiting:external` | Waits on someone outside the team. |
| `blocked` | Waits on another issue. Link it. |
| `needs-human` | An agent cannot go further without a person. |
| `agent-ready` | Clear enough for an agent to do with no more questions. |

## A change, step by step

**One issue, one branch, one pull request.** Do not stack pull requests on each other. Squash-merge rewrites the parent and breaks the child.

| # | Step | What to do |
| --- | --- | --- |
| 1 | Issue | Find or open the issue. Claim it. |
| 2 | Branch | From the latest `origin/main`. Name it `<person>/<type>/<topic>`, for example `robin/fix/venue-address`. |
| 3 | Change | Make the change. Run the repo's real checks. For a page, look at it on desktop and on a phone. |
| 4 | Commit | Small steps, [conventional commits](https://www.conventionalcommits.org/) (`fix: correct the venue address`). Add files by name, never `git add -A`. |
| 5 | Pull request | Open it as a **draft**. Write what changed and why, and `Closes #N`. Add a screenshot when a page looks different. An agent says in the body that an agent wrote it. |
| 6 | Checks | CI must be green. Read the CI log yourself; do not trust a one-line summary. |
| 7 | Review | Ask one other person or agent to look. Fix what matters. Write what you skipped and why. |
| 8 | Merge | Mark the pull request ready, then **Squash and merge**. Delete the branch. |

## How agents work together

Many agents can work in one repo at the same time. These rules keep them out of each other's way.

- **One lane per area.** An area is a folder or a feature. Two lanes never edit the same files.
- **Each lane has its own worktree** (`git -C <repo> worktree add ../<repo>-<topic> -b <branch> origin/main`), so lanes never share a working folder.
- **Say who the neighbours are.** A brief for a lane names the area, the neighbour lanes, and the files it must not touch.
- **The draft pull request is the claim** on its files. If a draft already touches them, talk to that lane first.
- **Hand work over with GitHub, not with chat.** Assign the issue to the next person and add a `waiting:*` label with a comment that says what they need to do.
- **Keep to a small number of open lane pull requests** per repo (five is a good limit), so review can keep up.
- **An agent reads its own CI logs, and does not say "done" without the evidence**: test output, what it checked, and what it did not check.
- **An agent never reviews or approves its own pull request.** Use a second agent or a person.

### What needs a person

An agent stops and asks a person for a yes before it does any of these:

- merge a pull request that touches login, permissions, CI, workflows, migrations or an admin surface (the repo's `CONTRIBUTING.md` lists these paths)
- run a database migration, or deploy by hand
- create, change or share a secret, a token or a permission
- change a hook, a guard or a security setting
- send a message, an email or a post to people outside the team
- write to live data

If the repo says a person lands every pull request, then the agent stops at "green and reviewed" and the person merges.

## Decisions

Decisions go in issue comments with the name and the date: `Mark, 18.11.2026: "use CHF 150 as the first price"`. A decision made in chat is not lost, but somebody copies it into the issue.

For a big open question with many parts, open one issue with the label `question` and list the smaller questions as a checklist.

## Tools that help

- The `undavos-github-flow` skill in [`undavos-agents`](https://github.com/unDavos/undavos-agents) teaches an agent these steps. This page is the short version of it.
- If you are unsure, ask in the issue. A question in an issue is never a waste.
