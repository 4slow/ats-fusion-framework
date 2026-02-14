# Upload to GitHub (Public Repo)

## 1) Create an empty repository on GitHub
- Name suggestion: `ats-fusion-framework`
- Visibility: **Public**
- Do **not** add README/license on GitHub (already included here)

## 2) Push from your PC (Windows PowerShell)

From this folder (the repo root):

```powershell
git init
git add .
git commit -m "Initial public framework (sim + optional TWS)"
git branch -M main
git remote add origin <PASTE_YOUR_GITHUB_REPO_URL>
git push -u origin main
```

## 3) Safety checks
- Ensure `.env` is NOT committed (it's in `.gitignore`)
- Only `.env.example` should be in the repo

## 4) Verify
On GitHub:
- README renders
- CI (if you add Actions later) is green
