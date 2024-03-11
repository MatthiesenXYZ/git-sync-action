# git-sync-action
A Simple action to Sync two git repos

The Following example will mirror ANY change to GitLab

```yml
name: Gitlab Sync

on:
  - push
  - delete

permissions: read-all

jobs:
  sync:
    runs-on: ubuntu-latest
    name: Git Repo Sync
    steps:      
    - uses: actions/checkout@v4
      with:
        fetch-depth: 0
    - uses: MatthiesenXYZ/git-sync-action@v1.1
      with:
        # Such as https://gitlab.com/matthiesenxyz/astro-ghostcms.git
        target-url: ${{ secrets.GITLAB_URL }}
        # Such as amatthiesen
        target-username: ${{ secrets.GITLAB_USERNAME }}
        # Create a Personal Access Token on gitlab.com and store it in GitHub Secrets as GITLAB_TOKEN
        target-token: ${{ secrets.GITLAB_TOKEN }}
```
