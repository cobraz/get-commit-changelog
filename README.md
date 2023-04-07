# get-commit-changelog

This GitHub Actions returns a list of commits between two commits as an output. This is useful when creating a changelog between two commits, such as when deploying something new to the servers, you might wanna give that a changelog. If you keep tabs of your head and base commits, this action might be useful for you!

## Features

- Uses [composite action][./action.yml]
- Commits can be typical container tags (e.g. branchname-69b7ea).
  **Note**: This action uses what is **after** the dash (-).
- Can be used with other repositories

**Important**: You must use a personal access token with repo scope if you're reading other repositories.

## Quickstart

```yaml
- uses: cobraz/get-commit-changelog
  id: changelog
  with:
    base: ${{ steps.something.base }}
    head: ${{ steps.something.head }}
- name: Print changelog
  run: echo "${{ steps.changelog.outputs.changelog }}"
```
