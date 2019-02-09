Git Advanced Notes
------------------
From [Learn Git Branching](https://learngitbranching.js.org/?demo)

- Graph
    - `git log --all --decorate --oneline --graph`

- Create And Switch To Branch
    - `git checkout -b <branchName>`

- Git Rebase
    - `git rebase <branch_to_rebase_on> <for_which_branch | HEAD>`
    - "Rebase me on <branchName>"

- Git Reset
    - `git reset <commitName/Relative>`
    - Move back in time as the commits after were not happened

- Git Revert
    - `git revert <commit>`
    - Make a commit that reverts back to the commit specified

- Git Cherry-Pick
    - `git cherry-pick <commit1> <commit2> ...`
    - Copys commits elsewhere and commits here

- Git Interactive Rebase
    - `git rebase -i <commit>`
    - Can: reorder, omit, combine commits
    - Will have a pop-up window that contains commits between HEAD and <commit>

- Git Tag
    - `git tag <tagName> <commit (default HEAD)>`

- Git Describe
    - `git describe [<ref> | HEAD]`
    - Output: `<tag>_<numCommits>_g<hash>`





- Misc
    - `git comit --amend`
        - To make a small change
