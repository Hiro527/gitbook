---
description: GitHub Pages, GitHub Actions and GitBook.
---

# How-to-do?

### 1. Link your GitHub account

![](<.gitbook/assets/image (1).png>)

* Select GitHub and push `Configure`
* Authenticate with GitHub and choose your repo to put your document.

![](<.gitbook/assets/image (3).png>)

* Push `Synchronize`

### 2. Enable GitHub Actions

* Follow this page to enable: \[Gitbook Action]\([https://github.com/marketplace/actions/gitbook-action](https://github.com/marketplace/actions/gitbook-action))

{% hint style="warning" %}
**IMPORTANT: You have to change \`gitbook-action.yml\` due to change of default repo name.**\
**See:** [**https://github.blog/changelog/2020-08-26-set-the-default-branch-for-newly-created-repositories/**](https://github.blog/changelog/2020-08-26-set-the-default-branch-for-newly-created-repositories/)****
{% endhint %}

```yaml
name: 'Gitbook Action Build'
on:
  push:
    branches:
      - main  # trigger branch
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - name: Checkout action
      uses: actions/checkout@v2
    - name: Gitbook Action           # https://github.com/ZanderZhao/gitbook-action/releases
      uses: ZanderZhao/gitbook-action@v1.2.4  # -> or ZanderZhao/gitbook-action@master.  If not use master click above, use latest please 
      with:                                   #    or fork this repo and use YourName/gitbook-action@master
        token: ${{ secrets.PERSONAL_TOKEN }}  # -> remember add this in settings/secrets as following
        source_branch: main
```

### 3. Complete!

* Your GitBook is now published at \`https://{username}.github.io/{repo-name}\`
