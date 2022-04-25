# Contributing

## Releasing a new version

```shell
# Inputs
VERSION="{{THE NEW VERSION WITHOUT v PREFIX}}"
OLD_VERSION="{{THE PREVIOUS VERSION WITHOUT v PREFIX}}"

# Verify everything is fine
npx steadybit def-repo check

# Raise the version numbers in policy files
npx steadybit def-repo set-version -v "$VERSION"

# Raise the version numbers in README files
find . -name "README.md" | \
  tr '\n' '\0' | \
  xargs -0 -n1 sed -i "" -e "s/$OLD_VERSION/$VERSION/g"

# Commit
git add .
git commit -m "chore: release $VERSION"

# Set a git tag
git tag -a "$VERSION" -m "$VERSION"

git push --tags origin main
```