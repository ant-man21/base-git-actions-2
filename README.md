TODO
  - [ ] automerge does not work. it triggers after base repo merges but gets error
  - [ ] what about multiple submodules?
      - at the moment it only looks for the first submodule added to this repository. do we want it to hard look for certain submodules? should it just automatically find them?
  - [ ] type /merge in base PR to close PR (and submodule PRs) and automatically merge base and submodules (fixes submodule conflicts)
  - [ ] create PR drafts automatically (this is a nice to have imo)

DONE
  - [x] need to validate pr process and it works properly. (simple examples work. comment formatting is off and needs love)
  - [x] check to see if no submodules if it still works. (works) 
  - [x] change base PR check for submodule PRs.
      - Right now it is: check submodule PR exists and is closed
      - New: check is submodule PR exists, is opened, and is approved
  - [x] fix comment formatting
  - [x] scalability? is polling a good option every 5 minutes? (fixed with new fixes)