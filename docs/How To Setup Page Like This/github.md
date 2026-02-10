# Upload to GitHub

Once your project is initialized, you can version control it with Git and push it to GitHub.

## 1. Initialize Git

```bash
git init
git add .
git commit -m "Initial commit"
```

## 2. Create Repository

Use the GitHub CLI to create a new repository and push your code:

```bash
gh repo create rag-notes --source=. --remote=origin --push --public
```

*Note: If you encounter authentication or email privacy errors, verify your `gh` auth status and git config settings.*

## 3. Push Changes

If the initial push doesn't work or you need to set the upstream branch:

```bash
git push --set-upstream origin main
```
