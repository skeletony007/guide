## Using Git

**This document assumes you are using GitHub** (URLs are for GitHub)

🔑 Key
| Placeholder | Value                                                      |
| ---         | ---                                                        |
| `USERNAME`  | GitHub Login                                               |
| `REPO`      | The name of the GitHub repository that you want to work on |

### Clone a Git repository

- **Cone** a Git repository to the working directory
   ```
   git clone https://github.com/USERNAME/REPO.git
   ```

## Using Git step-by-step ⚙️

1. **Stage** the changes ready for a commit

   Use the `git add` command to stage a directory

   ```
   git add /path/to/REPO
   ```

   - you can use the `.` argument instead of a directory if the current
     directory is the one you want to commit

2. **Commit** changes to your local Git repository

   Use the `git commit` command to commit the staged changes with a commit
   message

   ```
   git commit -m <commit message>
   ```

3. **Push** your changes to a remote Git repository\*

   Use the `git remote` command to add the URL of the remote GitHub repository
   as a remote

   ```
   git remote add origin https://github.com/USERNAME/REPO.git
   ```

   - If you get the error message `error: remote origin already exists` when
     trying to add a remote to your Git repository, it means that a remote named
     "origin" has already been added to your repository. Execute

     ```
     git remote set-url origin https://github.com/USERNAME/REPO.git
     ```

     to fix this.

   - Note that you only need to do this if `origin` is not already
     https://github.com/USERNAME/REPO.git

     You can display the URL of the remote Git repository that is currently set
     as `origin`

     ```
     git remote get-url origin
     ```

   Use the `git push` command to upload commits to the remote Git repository.

   ```
   git push -u origin main
   ```

   - If you see something like `Resolving deltas: 100%`, then you have
     successfully pushed your changes.

   \* This step is not always necessary, but I have included it for
      completeness.

If you want to push more changes, you can execute

```
git add . ; git commit -m <commit message> ; git push --force
```

from `/path/to/REPO`

- Note that force pushing can overwrite changes on the remote repository, so it
  should be used with caution

### Git submdule

Here, `REPO` is the name of the repository you want to add as a submodule. I.e.
`/path/to/REPO` is a subdirectory of the current repository that is not yet 
created.

```
git submodule add https://github.com/USERNAME/REPO.git /path/to/REPO
```

To update the contents of the Git submodule, execute

```
git pull
```

from the submodule directory.

### Move your unsaved changes to a new branch without committing

1. Stash your changes

   ```
   git stash
   ```
2. Create a new branch

   ```
   git checkout -b <new_branch_name>
   ```
4. Apply your changes from the stash

   ```
   git stash apply
   ```
5. If you want to remove the changes from the stash, use

   ```
   git stash drop
   ```

### Create release tags (using semantic verioning)

```
git tag -a v2.7.45 -m "release 2.7.45"
git push <remote> v2.7.45
```

### Archive Git branches

Archive and delete the branch.

**Local**

- Create the tag and delete the branch

  ```
  git tag archive/<branchname> <branchname>
  git branch -d <branchname>
  ```
- (undo) Restore the branch and delete the tag

  ```
  git checkout -b <branchname> archive/<branchname>
  git tag --delete archive/<branchname>
  ```

**Remote**

- Push local tags to remote and delete remote branch

  ```
  git push <remote> archive/<branchname>
  git push -d origin <branchname>
  ```

- (undo) Push branch to remote and delete remote tag

  ```
  git push --set-upstream <branchname>
  git push --delete origin archive/<branchname>
  ```

### Undo things 📜

> [How to undo (almost) anything with Git] (See <https://stackoverflow.com/q/15772134>)
>
> [Learn how to rewrite Git history] (unofficial)

#### Interactive rebase

To use Reword, Delete, Reorder\*, Squash and Split:

```
git rebase -i HEAD~n  ## replace `n` with the number of commits to show (from the latest)
```

**Note** that interactive rebase shows commits in reverse chronological order.

\* To reorder, literally change the line order in the file

#### The latest commit

To add untracked files to the last commit:

```
git add <untracked files>
git commit --amend --no-edit
```

To change the commit message, just replace `--no-edit` with `-m <message text>`

#### Accidental severe repository damage

Execute

```
git reflog
```

to find the desired branch state commit code (e.g. c9ff7ca).

Then execute

```
git reset --hard <commit code>
```

Use `git push -f`.

#### Remove all commits from a branch and maintain the current state

1. Checkout a new orphan branch

```
git checkout --orphan <tmp_branch_name>
```

2. Stage all files

```
git add -A
```

3. Commit

```
git commit -m <commit message>
```

4. Delete the old branch and rename the new branch

```
git branch -D <selected_branch_name>
git branch -m <selected_branch_name>
```

#### When is `push -f` necessary?

`git push -f` can be used to overwrite history at the remote branch.

## Removing a local clone of a repository

When you're done with a repository and don't want it taking up space, here's
what to do.

Execute

```
cd /workspaces ; rm -rf /workspaces/REPO ; rm -f /workspaces/ID/REPO
```

`-r` "recursive"

`-f` "force" (suppress confirmation messages)

### Links

[So You Think You Know Git - FOSDEM 2024]

[GitHub gpg keys page]


[How to undo (almost) anything with Git]: (https://github.blog/2015-06-08-how-to-undo-almost-anything-with-git/)
[So You Think You Know Git - FOSDEM 2024]: https://youtu.be/aolI_Rz0ZqY
[GitHub gpg keys page]: https://docs.github.com/en/authentication/managing-commit-signature-verification/generating-a-new-gpg-key
[Learn how to rewrite Git history]: https://youtu.be/ElRzTuYln0M
