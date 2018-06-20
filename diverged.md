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
