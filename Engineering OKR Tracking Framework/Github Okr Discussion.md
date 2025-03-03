# 📌 Automate Pulling OKRs into a GitHub Discussion

## 🚀 Introduction
This script automates the retrieval of **OKRs stored as Issues** in a GitHub repository, formats them into a summary, and posts them into a **GitHub Discussion** for better team visibility and tracking.

---

## 🛠 How It Works
1. **Fetches OKRs**: Queries issues labeled as **"OKR"** from the repo.
2. **Formats them into a summary**: Extracts key details and links to the issues.
3. **Posts them into a GitHub Discussion**: Uses GraphQL API to create a new discussion.

---

## 📌 Python Script
```python
import requests  

# GitHub API and repo details
GITHUB_TOKEN = "your_personal_access_token"
OWNER = "your-org-or-username"
REPO = "your-repo-name"
DISCUSSION_CATEGORY_ID = "your-discussion-category-id"  # Must retrieve from API

# GitHub API endpoints
ISSUES_URL = f"https://api.github.com/repos/{OWNER}/{REPO}/issues"
DISCUSSIONS_URL = f"https://api.github.com/graphql"

# Headers for authentication
HEADERS = {
    "Authorization": f"Bearer {GITHUB_TOKEN}",
    "Accept": "application/vnd.github.v3+json",
}

# Fetch OKR-related issues
def get_okrs():
    response = requests.get(ISSUES_URL, headers=HEADERS, params={"labels": "OKR"})
    issues = response.json()
    
    okr_list = []
    for issue in issues:
        okr_list.append(f"- **[{issue['title']}]({issue['html_url']})**: {issue['body'].splitlines()[0]}")
    
    return "\n".join(okr_list)

# Create GitHub Discussion
def create_discussion():
    okr_summary = get_okrs()
    
    query = """
    mutation {
      createDiscussion(input: {
        repositoryId: "your-repository-id",
        categoryId: "%s",
        title: "OKR Summary - Weekly Update",
        body: "### 🚀 OKR Weekly Summary\n\n%s\n\n### 📅 Next Steps\n- [ ] Review OKRs in next sync\n- [ ] Assign owners for flagged OKRs"
      }) {
        discussion {
          url
        }
      }
    }
    """ % (DISCUSSION_CATEGORY_ID, okr_summary)

    response = requests.post(
        DISCUSSIONS_URL, headers=HEADERS, json={"query": query}
    )
    print(response.json())

# Run the automation
create_discussion()
```

---

## 🔗 Setup Notes
- Generate a **GitHub Personal Access Token (PAT)** with `repo` and `discussions` scopes.
- Replace `your-org-or-username`, `your-repo-name`, and `your-repository-id` with actual values.
- Retrieve the **Discussion Category ID** using GitHub’s API (or manually from an existing discussion).

---

## 📂 Additional Resources
- [GitHub Discussions Guide](https://docs.github.com/en/discussions)
- [GitHub GraphQL API](https://docs.github.com/en/graphql)

🚀 _Let’s make OKRs transparent, actionable, and automated!_
