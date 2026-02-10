# Deploy to GitHub Pages

MkDocs makes it easy to deploy your documentation to GitHub Pages using the `gh-deploy` command.

## 1. Deploy Command

To build and deploy your site:

```bash
uv run mkdocs gh-deploy
```

This command will automatically:
1. Build your static site.
2. Commit the result to the `gh-pages` branch.
3. Push that branch to GitHub.

## 2. Verify Deployment

After a few moments, your site should be live at:
`https://<username>.github.io/<repo-name>/`

For example:
https://Rishita95.github.io/rag-notes/

## 3. Troubleshooting

If the site doesn't appear:
- Check the **Settings > Pages** section in your GitHub repository.
- Ensure the source is set to the `gh-pages` branch.
