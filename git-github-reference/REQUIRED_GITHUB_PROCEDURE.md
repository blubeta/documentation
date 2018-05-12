![blubeta](https://blubeta.com/images/b_Icon.svg)

# blubeta Git Requirments

# GOAL 
- Remove ourselves from local work
- Commit ourselves to deadlines ad peer review
- Break the chains of comfort with continued iteration

# EVERY MORNING
- DELETE entire repo (rm -rf /home/user/Desktop/local_dev/repo)
- PULL brand new from master, develop and ANY feature branches working on
- REBASE develop onto your feature branches
- REBASE master onto your hotfixes

# EVERY EVENING 

- POP all stashed changes
- COMMIT all work worthy of saving
- PUSH all work to relevent remote branches (origin/branch)

# BEFORE PULL REQUEST

All Features must be rebased onto develop

VETO
If it doesn't work in the happy path, it never worked.
If it doesn't work in the sad path, DOCUMENT what did you miss.

ACCEPTED

All Hotfixes must be rebased onto the develop branch IMMEDIATELY after being applied to master.



The code below will save your life.
- git config --global pull.rebase true
