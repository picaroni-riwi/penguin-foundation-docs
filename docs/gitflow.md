# Gitflow

This document explains how we use branches. Everything is written in English.

## The branches

| Branch | Purpose | Who writes to it |
|--------|---------|------------------|
| `main` | Stable code. This is what is published on GitHub Pages. | Nobody directly. Only the lead, through a PR from `develop`. |
| `develop` | Integration branch. Finished issues are combined and tested here. | Nobody directly. Only through PRs from issue branches. |
| `H-<issue>/<name>` | Your personal branch for one issue. | You, only your own branch. |

## Naming rule for issue branches

```
H-<issue number>/<your name>
```

Examples:

```
H-12/juandavid
H-15/eduardo
H-18/nicolas
H-21/santiago
```

Rules:

- Start with a capital `H-`, then the issue number.
- Use a slash `/` after the number.
- Your name in lowercase, no spaces, no accents.
- Use dashes `-`, never spaces. `H 12/juandavid` is wrong.
- Always use the same name.

## The flow

```
main      ●─────────────────────────────────●   PR from develop (lead approves)
           \                               /
develop     ●────────●─────────●──────────●      PRs from issue branches (lead approves)
             \      /           \        /
H-12/juandavid  ●──●              |      |
H-15/eduardo                      ●──────●
```

## Rules of the flow

1. Every issue gets its own branch, created from `develop`.
2. Your branch is yours only. Do not work on someone else's branch.
3. When your work is ready, open a PR **into `develop`**.
4. The lead reviews and approves. You do not continue on that branch until the review is done.
5. When a milestone is finished and tested in `develop`, the lead opens a PR from `develop` into `main`.

## Step by step

### Step 1: Update `develop`

```bash
git checkout develop
git pull origin develop
```

### Step 2: Create your issue branch from `develop`

```bash
git checkout -b H-12/juandavid
```

### Step 3: Work and save in small steps

```bash
git status
git add .
git commit -m "feat(donation): add amount selector"
```

See [commit-conventions.md](commit-conventions.md).

### Step 4: Send your branch to GitHub

```bash
git push -u origin H-12/juandavid
```

Use `-u` only the first time. After that, `git push` is enough.

### Step 5: Open a Pull Request into `develop`

1. On GitHub, click **Pull requests** → **New pull request**.
2. **Base:** `develop`. **Compare:** `H-12/juandavid`.
3. Write the title in English, for example `feat(donation): add amount selector`.
4. In the description, write: the issue it solves (`Closes #12`), what changed, and how to test it.
5. Click **Create pull request**. GitHub assigns the lead as reviewer automatically.

### Step 6: Wait for approval

- Do not merge your own PR.
- If the lead asks for changes, fix them in the **same branch** and push. The PR updates by itself:

```bash
git add .
git commit -m "fix(donation): correct amount label"
git push
```

### Step 7: After the PR is merged

Delete the branch on GitHub (there is a button after merging), then clean your computer:

```bash
git checkout develop
git pull origin develop
git branch -d H-12/juandavid
```

## Milestone: from `develop` to `main`

Done only by the lead.

1. Test the site in `develop`: navigation, pages, links, and the Quality checklist in `index.html`.
2. Open a PR with **base `main`** and **compare `develop`**.
3. Write the description with the issues included and what was tested.
4. Review the changed files, then approve and merge.

## Command reference

| I want to... | Command |
|--------------|---------|
| See the branch I am on | `git branch` |
| See all branches, including remote | `git branch -a` |
| Switch to develop | `git checkout develop` |
| Update develop | `git pull origin develop` |
| Create my issue branch | `git checkout -b H-<issue>/<name>` |
| Switch to an existing branch | `git checkout H-<issue>/<name>` |
| See changed files | `git status` |
| Prepare all changes | `git add .` |
| Save a commit | `git commit -m "type(scope): description"` |
| Send my branch to GitHub | `git push -u origin H-<issue>/<name>` |
| Send more commits | `git push` |
| Delete my local branch after merge | `git branch -d H-<issue>/<name>` |
| Delete a remote branch | `git push origin --delete H-<issue>/<name>` |
| Undo the last commit, keep the changes | `git reset --soft HEAD~1` |
| Save unfinished work temporarily | `git stash` |
| Bring stashed work back | `git stash pop` |

## Conflicts

A conflict happens when two people change the same lines. It is normal.

1. Run `git status`. Files marked **both modified** have conflicts.
2. Open the file. You will see markers like `<<<<<<<`, `=======`, and `>>>>>>>`.
3. Keep the correct code, delete the markers, and save.
4. Then run:

```bash
git add <file>
git commit -m "fix(<scope>): resolve merge conflict"
git push
```

If you are not sure, ask before you continue.

## Common mistakes

- **Starting a branch from `main`.** Always start from `develop`.
- **PR with base `main`.** Your PR base must be `develop`.
- **Working on someone else's branch.** Check with `git branch` first.
- **Pushing to `develop` or `main` directly.** Use a PR.
- **Continuing before approval.** Wait for the lead.
- **Writing in Spanish.** Everything is in English.
- **Forgetting to pull.** Run `git pull origin develop` before creating a branch.