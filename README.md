# autoupdate-branch

[![Project Status: Active – The project has reached a stable, usable state and is being actively developed.](https://www.repostatus.org/badges/latest/active.svg)](https://www.repostatus.org/#active)

A github action to auto update branches (with enabled auto merge option) with base branch.

Action can do great work with Github automerge feature: [Automatically merging a pull request
](https://docs.github.com/en/github/collaborating-with-issues-and-pull-requests/automatically-merging-a-pull-request)


## Usage
- Add workflow to setup Github Actions:
```yaml
jobs:
  update-branches:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v2
      - name: Update branches
        uses: brainly/autoupdate-branch
        id: autoUpdateBranch
        with:
          repo-token: "${{ secrets.GITHUB_TOKEN }}"
          requiredApprovals: 1 #Number of required approvals before branch should be updated

```
- PR which has enabled auto merge will be automatically updated

## Outputs
This action also returns some output in case you would like to use this in your workflow:
```yaml
outputs:
  hasConflicts:
    description: 'Says if PR is conflicted'
  conflictedPullRequestJSON:
    description: 'data of conflicted PR in JSON in shape {title: string, url: string, user: {login, url, avatarUrl}}'
```
