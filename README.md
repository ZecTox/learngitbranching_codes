# learngitbranching_codes
My answers to all the problems in the [learngitbranching.js.org](https://learngitbranching.js.org/)
> [!NOTE]
> I've used `git checkout` but you can use `git switch` instead of checkout.
------------------------------------------------------------------------
# GIT MAIN SECTION
## Introduction Sequence
### 1: Introduction to Git Commit
```
git commit
git commit
```

### 2: Branching in Git
```
git checkout -b bugFix
```

### 3: Merging in Git
```
git checkout -b bugFix
git commit
git checkout main
git commit
git merge bugFix
```

### 4: Rebase Introduction
```
git checkout -b bugFix
git commit
git checkout main
git commit
git checkout bugFix
git rebase main
```

## Ramping Up
### 1: Detach yo' HEAD
```
git checkout c4
```

### 2: Relative Refs (^)
```
git checkout HEAD^
```

### 3: Relative Refs #2 (~)
```
git checkout HEAD^
git branch -f main c6
git branch -f bugFix c0
```

### 4: Reversing Changes in Git
```
git reset local^
git checkout pushed
git revert pushed
```

## Moving Work Around
### 1: Cherry-pick Intro
```
git cherry-pick c3 c4 c7
```

### 2: Interactive Rebase Intro
```
git rebase -i HEAD~4
```

## A Mixed Bag
### 1: Grabbing Just 1 Commit
3 different answers that I find to solve the problem 
```
git branch -f bugFix c1
git cherry-pick c4
git branch -f main c4'
```
OR
```
git rebase -i main
git branch -f main c4'
```
OR - ***************BEST Solution***************
```
git rebase -i HEAD~3
git branch -f main c4'
```

### 2: Juggling Commits
```
git rebase -i HEAD~2
git commit --amend
git rebase -i HEAD~2
git branch -f main c3''
```
OR
```
git rebase -i HEAD~2
git rebase -i HEAD~1
git rebase -i HEAD~2
git branch -f main c3''
```

### 3: Juggling Commits #2
```
git checkout main
git cherry-pick c2
git rebase -i HEAD~1
git cherry-pick c3
```
OR - ***************BEST Solution***************
```
git checkout main
git cherry-pick c2
git branch -f main c1
git cherry-pick c2' c3
```

### 4: Git Tags
```
git tag v0 c1
git tag v1 c2
git checkout c2 (OR) git checkout main^
```

### 5: Git Describe
```
git describe main     #output: v0_2_gC2
git describe side     #output: v1_1_gC4
git describe bugFix   #output: v1_2_gC6
```

## Advanced Topics
### 1: Rebasing over 9000 times
```
git checkout bugFix
git rebase c2
git checkout main
git branch -f main c4
git rebase c3'
git branch -f main c5
git rebase c4'
git branch -f main c6
git rebase c5'
git branch -f main c7
git rebase c6'
git branch -f another c7'
git branch -f side c6'
```
OR
```
git rebase main bugFix
git rebase bugFix side
git rebase side another
git branch -f main c7'
```
OR - ***BEST Soltion***
```
git rebase main bugFix
git rebase bugFix side
git rebase side another
git rebase another main
```

### 2: Multiple parents
```
git branch -f bugWork c2
```
OR - ***BEST Soltion***
```
git branch bugWork main~^2~
```

### 3: Branch Spaghetti
```
git rebase -i one main
git  branch -f main c5
git rebase -i one main
git branch -f main c5
git branch -f one c2'
git branch -f two c2''
git branch -f three c2
git checkout two
```
OR - ***BEST Solution***
```
git checkout one
git cherry-pick c4 c3 c2
git checkout two
git cherry-pick c5 c4 c3 c2
git branch -f three c2
```
------------------------------------------------------------------------------------
# GIT REMOTE SECTION
## Push & Pull -- Git Remotes!
### 1: Clone Intro
```
git clone
```

### 2: Remote Branches
```
git commit
git checkout o/main
git commit
```

### 3: Git Fetchin'
```
git fetch
```

### 4: Git Pullin'
```
git fetch
git merge o/main
```
OR - ***BEST solution***
```
git pull
```

### 5: Faking Teamwork
```
git clone
git fakeTeamwork main 2
git commit
git pull
```
OR
```
git clone
git commit
git fakeTeamwork main 2
git pull
```

### 6: Git Pushin'
```
git commit
git commit
git push
```

### 7: Diverged History
```
git clone
git fakeTeamwork main
git commit
git fetch
git rebase o/main
git push
```
OR - ***BEST Solution***
```
git clone
git fakeTeamwork main
git commit
git pull --rebase
git push
```

### 8: Locked Main
```
git checkout -b feature
git branch -f main c1
git push
```
OR - ***BEST Solution***
```
git reset o/main
git checkout -b feature c2
git push      # Can also use- git push origin main 
```

## To Origin And Beyond -- Advanced Git Remotes!
### 1: Push Main!
```
git branch -f side3 c1
git pull origin main
git cherry-pick c2 c3 c4 c5 c6 c7
git branch -f side1 c2'
git branch -f side 2 c4'
git branch -f main c7'
git push origin main
```
OR - ***BEST Solution***
```
git fetch     #Can also use- git fetch origin main
git rebase o/main side1
git rebase side1 side2
git rebase side2 side3
git rebase side3 main
git push      #Can also use- git push origin main
```

### 2: Merging with remotes
```
git checkout main
git pull origin main
git merge side1
git merge side2
git merge side3
git push origin main
```

### 3: Remote Tracking
```
git checkout -b side o/main
git commit
git pull --rebase
git push
```

### 4: Git push arguments
```
git push origin main
git push origin foo
```

### 5: Git push arguments -- Expanded!
```
git push origin main^:foo
git push origin foo:main
```

### 6: Fetch arguments
```

```

### 7: Source of nothing
```

```

### 8: Pull arguments
```

```
