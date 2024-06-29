# Create Release From Tag

This action checks out the repository, and creates a tag from the latest commit. If the tag is created, it creates a release from the tag. It also uses `changelogithub` action to generate changelog from the tag.

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
