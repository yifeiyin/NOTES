# Git Handy Operations

## Branching
- View
  - `git branch`
  - `git branch -a` show all remote-tracking branches and local branches

- Create
  -  `git checkout -b <new_branch_name>`

- Using
  - Switch to `git checkout <branch_name>`
  - Merge a branch to HEAD `git merge <from_branch_name>`

- Delete
  - delete locally `git branch -d <branch_name>`
  - Note: use `-D` to force delete regardless of merge status

- Sharing
  - Push to remote `git push -u <origin_name> <branch_name>`
  - Delete a remote branch `git push <origin_name> --delete <branch_name>`





## Discard Files
- Discard one file, to HEAD `git checkout <file_name>`
    - When file name is in conflict with a branch name, use `git checkout -- <file_name>`
- Revert all file, to HEAD `git reset --hard`
    - Use with caution!

- `git reset --soft <commit>`
    - leaving files alone, changing branch head to some commit






## Tag
- lightweight tag, anotated tag
  - lightweight tag is a alias for a commit
  - anotated tag is an object in git, contains a lot more information (email, message, date, etc)

- View
  - `git tag`
  - `git tag --list <pattern>` `-l for short`

- Create lightweight tag
  - `git tag <new_tag_name> [commit|head]`

- Create annotated tag
    - `git tag -a <new_tag_name> [commit|head] [-m <message>]`
- Delete
    - `git tag -d <tag_name>`

- Sharing
  - `git push origin <tag_name>` push one tag
  - `git push origin --tags` push all local tags
  - Note: this will push all kinds of tags, there is no easy way to push one type of tag
  - `git push origin --delete <tag_name>` delete remote tag




## General Git Notes
- `index` refers to the staging area
- `working tree` refers to the working directory



## Miscellaneous

- `git add -p` `--patch` (`--interactive` implied) to manually select hunks

