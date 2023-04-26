# Branching

## Permanent branches

* `main` is the default branch
* `dev` branch is not used
* tags are used for each release
  - Example `2.10.4`
* `release` branches are not used

## Temporary branches

All temp branches are branched from `main` and merged into `main`.

* `feat` branches add a feature
  - Example: `feat-react-messages`
* `fix` branches fix an issue
  - Example: `fix-grpc-contracts`
* `cicd` branches are related to CICD only
  - Example: `cicd-update-docker-image`

# Merge strategy

* We want to have a good commit history that has self-contained commits
* We want to be able to refactor code
  - In order to facilitate the code change we're making
  - In order to practice continuous refactoring
  - This usually requires separate commits
* We don't want to have a large (merge) commit which combines changes in too many aspects

Decisions:

* Temporary branches should be merged using a fast-forward merge:
  - ~~Merge commit~~ is not accepted
  - ~~Squash merge~~ is not accepted
  - **Rebase** is preferred
* Use interactive rebase on the temp branch before/during creating a PR:
  - Avoid `Fix something` commit spamming which would pollute the permanent branch history
  - Make commits more self-contained
  - Only temp branches should be rebased by engineers and force-pushed-to
  - If more than 1 engineer works on a temp branch and one wants to force-push then they should coordinate
* Unfortunately with rebase it is not known if it's safe to checkout a specific commit in a permanent branch
  - Code may be in an intermediate state and not stable
  - Commits which are tagged should be checked out

# Commit message template

* Start with a verb
* Use **imperative** form (without -ed or -ing)
* Use `Upper Case` (not `lower case`)
* Focus on what the commit does
* For commits with details use 1 line intro ending in `:`, a blank line, and then a `*`-led list 

### 1 line commit:

```text
Add a new feature for reacting to chat messages
```

### Multi-line commit:

```text
Add a new feature for reacting to chat messages:

* Add new gRPC contracts
* Notify chat members
* Persist reactions into database
```

# PR requirements

* Mandatory
  - Good description (maybe with links) in order to help the reviewers
  - Successful CICD pipeline
* Changes
  - Update `CHANGELOG` when the PR changes reflect the end result
  - Increase the version number when the PR changes reflect the end result
  - PRs only modifying the CICD most probably don't change the end result
* Reviewing
  - PR creator is the Assignee
  - PR creator should check how its PR looks before assigning reviewers
  - At least 1 reviewer (who is another person!) should approve the PR
  - At least 1 code owner (who is another person!) should approve the PR
  - Possible exceptions: team size is small, there's no one available due to holidays/etc, there's an urgent need to merge changes
