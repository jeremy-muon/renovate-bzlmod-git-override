# 33748

## Current behavior

The only dependencies to update are `bzlmod` from `MODULE.bazel`.

Renovate correctly finds a new version for `rules_python`.

It fails to find a new version for `rules_cc`.

The error message is: "Could not determine new digest for update (github-tags package bazelbuild/rules_cc)"

It attempted to look up the commit at https://bcr.bazel.build/api/v3/repos/bazelbuild/rules_cc/commits?per_page=1 instead of at https://github.com/api/v3/repos/bazelbuild/rules_cc/commits?per_page=1. As described in the discussion, this appears to be a bug in [this function](https://github.com/renovatebot/renovate/blob/91f92c514d71a1a49cba52ea6d9a0a81f9d757e4/lib/modules/datasource/github-tags/index.ts#L38) which only occurs when using `.bazelrc` to specify a custom registry.

## Expected behavior

Correctly detect the new commit for `rules_cc`. This desired behavior can be achieved
by commenting out the registry flag in `.bazelrc`

## Link to the Renovate issue or Discussion

See [the discussion](https://github.com/renovatebot/renovate/discussions/33748)
