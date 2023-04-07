# get-commit-changelog

This action returns a list of commits between two commits as an output. This is useful when creating a changelog between two commits, such as when deploying something new to the servers, you might wanna give that a changelog. If you keep tabs of your head and base commits, this action might be useful for you!

## Features

- Uses [composite action](./action.yml)
- `base` and `head` can be typical container tags (e.g. branchname-69b7ea), because this action reads everything **after** a hyphen (-). Meaning, if you set `base` to `branchname-69b7ea`, it becomes `69b7ea`.
- Can be used with other repositories 📂
- Returns Markdown ✍️

**Important**: You must use a personal access token with repo scope if you're reading other repositories.

## Quickstart

```yaml
- uses: cobraz/get-commit-changelog
  id: changelog
  with:
    base: ${{ steps.something.base }}
- name: Print changelog
  run: echo "${{ steps.changelog.outputs.changelog }}"
```

Also, check out the [`test.yml`](.github/workflows/test.yml) for a real, working example. In this I have manually
set the `base` to the first commit in this repository. In theory, the changelog will contain all commits in this
repository. Check out [the actions tab](https://github.com/cobraz/get-commit-changelog/actions/workflows/test.yml) for example runs.

## Inputs

- `base` (**required**) is the typically the latest commit (the _to_ commit in our example).
- `head` (defaults to `github.ref`) is typically the commit back in time.
- `token` (defaults to `github.token`) is the GitHub token. It needs to be a personal GitHub token if you are trying to compare other repositories.
- `repository` (defaults to `github.repository`) is which GitHub repository you want to compare commits in.
