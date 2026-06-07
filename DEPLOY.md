# Deploy to GitHub Pages

Your site is ready to deploy. Follow these steps:

## 1. Create a GitHub Repository

If you don't have a repo yet:

1. Go to [github.com/new](https://github.com/new)
2. Name it (e.g., `my-website` or `portfolio`)
3. Choose **Public** (required for free GitHub Pages)
4. Click **Create repository**

Copy the HTTPS or SSH URL from the repo page.

## 2. Initialize Git & Push (Windows PowerShell)

From the **root folder** (`My website 2`), run:

```powershell
# Initialize repo if not already done
git init
git add .
git commit -m "chore: initial commit"

# Add remote (use the URL from step 1)
git remote add origin https://github.com/USERNAME/REPO.git
# or
# git remote add origin git@github.com:USERNAME/REPO.git

# Rename branch to main if needed, then push
git branch -M main
git push -u origin main
```

Wait a few seconds for the push to complete.

## 3. Configure GitHub Pages

1. Go to your repo on GitHub
2. Click **Settings** → **Pages**
3. Under **Source**, select:
   - Branch: `main`
   - Folder: `/ (root)` or `/docs`
4. Click **Save**

> If you choose `/docs`, GitHub will serve `docs/index.html` as your homepage.

## 4. Wait for the Site to Go Live

- GitHub will show a green checkmark + URL when ready (usually ~1–2 minutes)
- Visit the URL to see your live site
- The GitHub Actions workflow will auto-build and update `docs/` on every push

## 5. Update Content (Ongoing)

To update your site:

1. Edit content in `app/src/config.ts` or components
2. Push to main:
   ```powershell
   git add .
   git commit -m "chore: update content"
   git push origin main
   ```
3. GitHub Actions automatically rebuilds and updates `docs/`
4. Your site updates within 1–2 minutes

## Troubleshooting

- **Pages not showing?** Wait 2 minutes and hard-refresh (Ctrl+Shift+R)
- **Old content still showing?** Clear browser cache or use incognito mode
- **Build failed?** Check the **Actions** tab in your GitHub repo for error logs

## Advanced Options

- To serve from a subdirectory (e.g., `github.com/USERNAME/REPO`), update `vite.config.ts`:
  ```ts
  export default defineConfig({
    base: '/REPO/',  // replace REPO with your repo name
    // ...
  });
  ```
  Then rebuild: `cd app && npm run deploy:docs && git push origin main`

- For custom domain: add a `CNAME` file in the `docs/` folder (or root) with your domain, then configure DNS
