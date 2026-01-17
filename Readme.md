Git Rebase is a Git operation used to move or replay commits from one branch onto another branch, creating a linear and cleaner commit history by changing the base commit of a branch.
Rebase takes commits from one branch and reapplies them on top of another branch.
Rebase is used on feature branches to maintain a clean, linear history, 
🚨 Rebase rewrites history,so it should be used only on private or feature branches, not on shared branches like main.

commandds:
git checkout feature
git rebase main
git checkout main
git rebase feature OR git merge feature(safer no rewrites)

while merge is used on main branches to safely integrate changes without rewriting shared history.
Feature branch → rebase 
Main branch → merge 

git rebase

Purpose:
Clean and update a feature branch with latest main changes
Used on side/feature branches
Rewrites commit history
Keeps history linear and clean

git merge

Purpose:
Safely integrate completed work into main
Used on main / shared branches

Why we DO NOT rebase main (MOST IMPORTANT)
🚨 Rebase rewrites history

If you run:

git checkout main
git rebase navbar


Git will:

Change commit hashes of main
Rewrite shared history

This causes:
Teammates’ branches to break
Push conflicts
Force-push requirement
Confusion and data loss risk

That’s why rebasing main is dangerous
Preserves history

Team-safe operation

Visual mental model (simple)
Before
main     A---B---C
navbar          D---E

Rebase navbar
main     A---B---C
navbar              D'---E'

Merge into main
main     A---B---C---D'---E'

8️⃣ What happens if you rebase main? (danger case)
main     A---B---C
navbar          D---E

git checkout main
git rebase navbar


➡ main becomes:

A---B---C---D'---E'


⚠ Anyone else using main now has broken history.
