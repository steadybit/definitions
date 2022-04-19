# Contributing

## Releasing a new version

```shell
# Inputs
VERSION="{{THE NEW VERSION WITHOUT v PREFIX}}"

# Verify everything is fine
npx steadybit def-repo check

# Raise the version numbers in policy files
npx steadybit def-repo set-version -v "$VERSION"
git add .
git commit -m "chore: release $VERSION"

# Set a git tag
git tag -a "$VERSION" -m "$VERSION"

git push --tags origin main
```