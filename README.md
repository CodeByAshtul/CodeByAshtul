### Hi there 👋

<!--
**CodeByAshtul/CodeByAshtul** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->


import requests

def create_github_repository(repo_name, access_token):
    headers = {
        "Authorization": f"token {access_token}",
        "Accept": "application/vnd.github.v3+json"
    }

    data = {
        "name": repo_name,
        "auto_init": True,  # Set to False if you don't want to create an initial commit with README.
        # You can add more options like "private": True to create a private repository.
    }

    try:
        response = requests.post("https://api.github.com/user/repos", json=data, headers=headers)
        response.raise_for_status()
        print("Repository created successfully!")
        print(f"Repository URL: {response.json()['html_url']}")
    except requests.exceptions.RequestException as e:
        print("Error creating the repository:", e)

if __name__ == "__main__":
    # Replace with your GitHub username, repository name, and access token
    github_username = "your_github_username"
    repository_name = "your_repository_name"
    github_access_token = "your_github_access_token"

    create_github_repository(repository_name, github_access_token)
