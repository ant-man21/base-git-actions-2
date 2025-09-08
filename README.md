# How It Works:
Instead of manually linking PRs together, and manually merging them, the goal of these GitHub Actions is to automate these steps. After the developer makes thier changes, commits them, and pushes them to a branch, they will open a PR for the base repo and submodule repo. The github actions will handle approvals, links, and PR statuses. Onced Approved and ready to merge, the developer can trigger the merge github action to finally merge both base and submodule to thier main branches with proper fixing of submodule pointers. 

## The Developer Workflow: With Submodule Changes
- Developer makes changes, commits, and pushes to a branch for base repo and submodule repo (Note the branch name NEEDs to be the same for the repos.)
- Developer opens 2 Pull Requests. 1 for the base repo and 1 for the submodule repo. _(Theoretically can be automated too)_
- Then the github actions will link and do a series of checks to verify the proper completion of the PRs. It will:
  - Add comments to Base PR and Submodule PR with links to each other
  - Add labels and status message on checks tab for current PR status
  - Refuse merging to normal users if they have not fulfilled requirements. (PRs exist, are open, are approved, have no conflicts)
- At this point a devloper has approved PRs and is ready to merge. The merge github action can triggered manually.
  - Likely to be a notification about merge conflicts. specifically with submodule still
  - _(using /merge command as a comment is currently my idea but open to others)_ <-- only way I thought to handle submodule merge conflict automatically, other conflicts can be handled before approving PR

## The Developer Workflow: Without Submodule Changes
- Developer makes changes, commits, and pushes to a branch for base repo
- Developer opens a PR for base rpeo. Github action runs on PR open and see not submodules where changed and skips checks related to submodules
- Proceed as a typical single Repo PR (approvals, merge conflicts) and merge with Green merge button

TODO
  - [ ] automerge does not work. it triggers after seeing /merge comment but gets error
  - [ ] what about multiple submodules?
      - at the moment it only looks for the first submodule added to this repository. do we want it to hard look for certain submodules? should it just automatically find them?
  - [x] type /merge handling in base PR to close PR
  - [ ] create PR drafts automatically (this is a nice to have imo)

DONE
  - [x] need to validate pr process and it works properly. (simple examples work. comment formatting is off and needs love)
  - [x] check to see if no submodules if it still works. (works) 
  - [x] change base PR check for submodule PRs.
      - Right now it is: check submodule PR exists and is closed
      - New: check is submodule PR exists, is opened, and is approved
  - [x] fix comment formatting
  - [x] scalability? is polling a good option every 5 minutes? (fixed with new fixes)

Duplicate Line Change goes here!