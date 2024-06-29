# Create Github Release From Tag Action
This action has the following steps:
1. Check out the repository.
2. Create a tag based on `package.json` version number (only if the tag does not already exist).
3. Create a github release from the tag using [changelogithub](https://github.com/antfu/changelogithub) action and include changelog in the release body.

> This action requires the `package.json` file to be present in the root of the repository.

> This action also uses `pnpx` to run `changelogithub` action.


## Inputs
### `GITHUB_TOKEN`
**Required**. The GitHub token to use for authentication.

## Example usage
```yaml
name: Tag and publish release

on:
  push:
    branches:
      - master
    paths:
      - package.json
jobs:
  tag-npm-release:
    name: Tag and publish github release
    runs-on: ubuntu-latest

    steps:
       - name: Create Release From Tag
         uses: abdul-alhasany/actions/create-gh-release@main
         with:
           GITHUB_TOKEN: ${{secrets.GITHUB_TOKEN}}
```
