### Diverged Branch
1. Checkout a new branch
`git checkout -b diverged`

2. Edit readme file
`vim README.md`

3. Add and commit
```
git add README.md
git commit
```

4. Do more work (add and commit)

* Graphic
This it roughly what the current tree may look like
(The letters used are commits but are only used to express the look of the current branching. Not specific commits)
```
A--E           <- master
 \
  B--C--D   <- diverged
```

5. Ensure you are on the correct branch
`git checkout nonDiverged`

6. Update the current branch with master by rebasing (but don't rebase a shared branch. It causes problems)
`git rebase master`

* Graphic
This is roughly what the current tree may look like
```
A--E           <- master
    \
     B--C--D   <- diverged
```

* If merge conflict from rebase
    If you have a merge conflict from the rebase which is potential then fix the conflicts.
    Add the changes.
    Then run `git rebase --continue`.

7. Checkout a new branch (this will be the branch that is squashed)
(`c0` is used to represent a candidate branch)
`git checkout -b nonDiverged-c0`

* Graphic
This is roughly what the current tree may look like
```
A--E           <- master
    \
     B--C--D   <- diverged, diverged-c0
```

8. Now squash the commits
`git rebase --interactive master`

This opens an editor which to keep and which to squash (the file is read from top to bottom).

```
pick <commit id> B
squash <commit id> C
squash <commit id> D
```

Git will now merge all the squash commits into the pick

And will ask for a commit message

```
Add Non-Diverged section to README.md

* Add Non-Diverged Branch section
* Add step 4 and graphic to Non-Diverged Branch
* Add steps, graphic and fix previous graphic
```
It is a good idea to have a mini list like above of the commit titles that were squashed. This is so that you don't lose history. And the commit title for this one should be over all what this commit does.

* Graphic
This is rouphly what the current tree may look like

```
A--E           <- master
|   \
|    B--C--D   <- nonDiverged
 \
  F            <- nonDiverged-c0
```

9. Merge to master
This will move the current commit on this branch to master
```
git checkout master
git merge nonDiverged-c0 master
```

* Graphic
This is roughly what the current tree may look like

```
A--E--F        <- master, nonDiverged-c0
 \
  B--C--D   <- nonDiverged
```
