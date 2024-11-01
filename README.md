# learngitbranching_codes
My answers to all the problems in the learngitbranching.js.org

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
