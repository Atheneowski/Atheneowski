# ⏳ Automate OKR Updates with GitHub Actions

## 🚀 Introduction
This GitHub Actions workflow automates the process of **fetching OKRs from Issues** and posting updates into a **GitHub Discussion** on a scheduled basis. This ensures teams always have an up-to-date summary without manual effort.

---

## 📌 How It Works
1. **Runs on a schedule**: Automatically executes weekly (every Monday at 12:00 UTC).
2. **Fetches OKRs**: Retrieves issues labeled **"OKR"** from the repository.
3. **Posts updates into a GitHub Discussion**: Uses GitHub’s GraphQL API to create a structured summary.

---

## 📂 GitHub Actions Workflow File
Create a new file in your repository:  
📂 `.github/workflows/okr_discussion.yml`

```yaml
name: Weekly OKR Discussion Update

on:
  schedule:
    - cron: '0 12 * * 1' # Runs every Monday at 12:00 UTC
  workflow_dispatch: # Allows manual trigger

jobs:
  update-okr-discussion:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Repository
        uses: actions/checkout@v3
      
      - name: Set up Python
        uses: actions/setup-python@v3
        with:
          python-version: '3.x'
      
      - name: Install Dependencies
        run: pip install requests
      
      - name: Run OKR Discussion Script
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
        run: python your_script.py
```

---

## 🔑 Setup Instructions
1. **Store Your GitHub Token Securely**:
   - Go to **Settings > Secrets and variables > Actions**.
   - Click **New Repository Secret**.
   - Name it `GITHUB_TOKEN` and paste your **Personal Access Token (PAT)**.

2. **Modify Schedule (Optional)**:
   - Adjust the `cron` schedule based on your team’s reporting needs.
   - Example: Run every Friday at 9 AM UTC → `cron: '0 9 * * 5'`

3. **Ensure Your Script is Available**:
   - Commit a Python script (`your_script.py`) that pulls OKRs and posts them to GitHub Discussions.

---

## 📂 Related Resources
- [GitHub Actions Guide](https://docs.github.com/en/actions)
- [GitHub Discussions API](https://docs.github.com/en/graphql)
- [GitHub Secrets Guide](https://docs.github.com/en/actions/security-guides/encrypted-secrets)

🚀 _Let’s make OKRs automated, trackable, and actionable!_
