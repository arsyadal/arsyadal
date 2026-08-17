# 🛠️ Troubleshooting & FAQ

Common errors encountered when customizing GitHub profiles and how to fix them.

---

### 1. Snake Action Fails with `403 Resource not accessible by integration`
* **Cause:** By default, GitHub Actions workflows have read-only permissions in the repository.
* **Fix:** Add `permissions: contents: write` at the top level of your workflow `.github/workflows/snake-contribution.yml`:
```yaml
permissions:
  contents: write
```

---

### 2. Snake Image Not Showing / Broken Image `[?]`
* **Cause:** The workflow has not run yet, or the `output` branch has not been created.
* **Fix:** 
  1. Go to your repository on GitHub.
  2. Click the **Actions** tab.
  3. Select **Generate Contribution Snake Animation**.
  4. Click **Run workflow** manually to generate the first SVG commit.

---

### 3. GitHub Readme Stats Shows `Maximum request limit reached`
* **Cause:** The shared public instance of `github-readme-stats` has exceeded GitHub unauthenticated rate limits.
* **Fix:** Self-host your own instance in 2 minutes on Vercel:
  1. Fork the [anuraghazra/github-readme-stats](https://github.com/anuraghazra/github-readme-stats) repo.
  2. Deploy to [Vercel](https://vercel.com).
  3. Add an environment variable `PAT_1` with your personal GitHub Personal Access Token.
  4. Replace `github-readme-stats.vercel.app` in your README with `your-project.vercel.app`.

---

### 4. Blog Posts Workflow Not Updating
* **Cause:** Missing placeholder comments in `README.md`.
* **Fix:** Ensure your `README.md` contains the exact comment markers:
```markdown
<!-- BLOG-POST-LIST:START -->
<!-- BLOG-POST-LIST:END -->
```
The GitHub Action looks specifically for these comment delimiters to inject RSS posts.
