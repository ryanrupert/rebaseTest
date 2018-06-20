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
