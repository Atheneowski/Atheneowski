# 📂 In this bountiful folder

## 🚀 Overview
This repository contains templates and automation scripts to help teams **define, track, and manage OKRs** within GitHub. It provides structured resources for:
- **Tracking OKRs using GitHub Issues & Discussions**
- **Automating OKR updates with GitHub Actions**
- **Standardizing team communications with GitHub Discussions Templates**

---

## 📂 Available Resources

### 🔄 OKR Tracking & Discussion Automation
- **[OKR Tracking Framework](OKR%20Tracking%20Framework.md)**: A structured framework for defining and measuring OKRs.
- **[Automate OKR Updates with GitHub Actions](Automate%20OKR%20Updates%20with%20GitHub%20Actions.md)**: A scheduled GitHub Actions workflow to automate OKR discussions.
- **[GitHub Discussions Template](General%20GitHub%20Discussions%20Template.md)**: A structured template for team discussions and OKR rollups.
- **[GitHub OKR Discussion Automation](Github%20Okr%20Discussion.md)**: A Python script to pull OKRs from Issues and post them into GitHub Discussions.

---

## 🔧 Setup & Usage
### ✅ Setting Up GitHub Actions
1. **Store Your GitHub Token Securely**:
   - Navigate to **Settings > Secrets and variables > Actions**.
   - Click **New Repository Secret**.
   - Name it `GITHUB_TOKEN` and paste your **Personal Access Token (PAT)**.

2. **Modify Schedule (Optional)**:
   - Adjust the `cron` schedule in `.github/workflows/okr_discussion.yml` to fit your reporting needs.

3. **Ensure Your Script is Available**:
   - Commit and reference your Python script (`your_script.py`) in the workflow.

---

## 🔗 Additional Resources
- [GitHub Actions Guide](https://docs.github.com/en/actions)
- [GitHub Discussions API](https://docs.github.com/en/graphql)
- [GitHub Secrets Guide](https://docs.github.com/en/actions/security-guides/encrypted-secrets)

🚀 _Let’s make OKR tracking seamless, automated, and actionable!_
