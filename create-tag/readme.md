# Create Tag Action
This action creates a git tag based on `package.json`. It is based on [neverendingqs/gh-action-tag-on-npm-version@master](https://github.com/neverendingqs/gh-action-tag-on-npm-version).

## Inputs
### `git-user-email`
**optional**. The email address to use for the git user.

### `git-user-name`
**optional**. The name to use for the git user.

### `prefix`
**optional**. The prefix to use for the tag. Default is `v`.

## Outputs
### `tag`
The tag that was created.

### `tag-created`
Boolean indicating if the tag was created.

## Example usage
```yaml
name: Tag on npm version

on:
  push:
	branches:
	  - master
	paths:
	  - package.json

jobs:
  tag-npm-version:
	name: Tag on npm version
	runs-on: ubuntu-latest

	steps:
	  - name: Checkout code
		uses: actions/checkout@v3

	  - name: Create Tag
	    id: create-tag
		uses: abdul-alhasany/actions/create-tag@main

	  - name: Show tag
	    if: steps.create-tag.outputs.tag-created == 'true'
	  	run: echo "Tag created: ${{ steps.create-tag.outputs.tag }}"
```