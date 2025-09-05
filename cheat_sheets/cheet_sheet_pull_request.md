# GitHub Pull Request Cheat Sheet

## Step-by-Step Guide

### 1. Fork and Clone (for external contributions)

```bash
# Fork the repository via GitHub web UI
git clone https://github.com/<your-username>/<repo-name>.git
cd <repo-name>
```

*If working within your team's org repo, just clone as usual.*

---

### 2. Add the Upstream Remote (if contributing externally)

```bash
git remote add upstream https://github.com/<original-owner>/<repo-name>.git
# To sync later, use:
git fetch upstream
git rebase upstream/main  # Prefer rebase for a clean history
```

---

### 3. Create a Feature Branch

```bash
git checkout -b my-feature-branch
```

*Use a descriptive branch name, e.g., `fix/login-bug`, `feat/add-dark-mode`.*

---

### 4. Make, Add, and Commit Your Changes

```bash
# Make edits, then:
git add .
git commit -m "Clear, specific message (e.g., Add validation to login form)"
```

*Write descriptive, atomic commits focused on a single topic.*

---

### 5. Sync Your Branch (before pushing)

```bash
git fetch upstream
git rebase upstream/main
```

*Resolve any conflicts before pushing.*

---

### 6. Push Your Branch to GitHub

```bash
git push origin my-feature-branch
```

---

### 7. Open a Pull Request (PR) on GitHub

- Go to your repository on GitHub.
- Click "**Compare & pull request**" or navigate to the **Pull Requests** tab.
- Set:
  - **Base**: The target branch (e.g., `main`, `dev`, or other project default) in the upstream repo.
  - **Compare**: Your branch (e.g., `my-feature-branch`).
- Fill in:
  - **Title**: Clear, short summary of the change.
  - **Description**: Purpose, overview of changes, links to relevant issues (use `Fixes #issue-number`), and any notes for reviewers.
- Assign reviewers and labels if appropriate.
- Mark as "**Draft**" if the PR is not ready for review.

---

### 8. Respond to Reviewer Feedback

- Address requested changes promptly.
- Update the PR with new commits, or amend/rebase as needed.
- Revise the PR description if the scope changes.

---

## Quick Reference Table

| Step             | Command or Action                                                    |
| :--------------- | :--------------------------------------------------------------------|
| Fork repo        | GitHub web: Click Fork (if external)                                 |
| Clone repo       | `git clone <url>`                                                    |
| Add upstream     | `git remote add upstream <upstream-url>`                             |
| Create branch    | `git checkout -b my-feature-branch`                                  |
| Edit/commit      | ``git add .`<br>`git commit -m "summary"``                           |
| Sync (rebase)    | ``git fetch upstream`<br>`git rebase upstream/main``                 |
| Push branch      | `git push origin my-feature-branch`                                  |
| Open PR          | GitHub web: PR from your branch into target branch                   |
| Respond/rebase   | Address feedback, rebase/update branch, force push if you rebased    |

---

## Pull Request Best Practices

- **Keep PRs focused:** One fix or feature per PR; avoid mixed concerns.
- **Write clear titles and descriptions.**
- **Reference issues:** Use `Fixes #123` or `Closes #456` to auto-close issues on merge.
- **Self-review:** Build/test locally before pushing; proofread your PR and commits.
- **Tests:** Add or update unit/integration tests as needed.
- **Follow project conventions:** Respect code style, guidelines, and branch naming patterns.
- **Assign reviewers/labels:** Tag relevant reviewers or teams, and use labels for context when project supports it.
- **Draft PRs:** Use drafts for early feedback on incomplete work.
- **Automate checks:** Set up CI to run tests, linters, and security scans on PRs.
- **Update regularly:** Keep your branch synced with base frequently to minimize conflicts.
- **Be responsive:** Engage with feedback and iterate until approval.

---

## Optional: GitHub CLI PR Workflow

If you prefer the command line, try the GitHub CLI:

```bash
gh pr create --base main --head my-feature-branch --fill
```

---

## Sample PR Template

```markdown
### What does this PR do?

* Concise description of the change.

### Why is it needed?

* Context, linked issues, or rationale.

### How was it tested?

* Details of tests run or added.

### Review notes

* Anything specific for reviewers: areas of concern, review order, etc.
```
