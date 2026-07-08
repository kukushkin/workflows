# Workflows

Reusable workflows for GitHub Actions.

## github-release.yaml

Creates a GitHub release:
* Calculates a new version
* (optional) Writes the version to a VERSION.txt file
* Creates a new GitHub release

Inputs:
* `write_version`: (boolean) Whether to write the version to a VERSION.txt file, defaults to `false`.
* `version_filename`: (string) The path to the VERSION.txt file, defaults to `VERSION.txt`.

## How the versions are calculated

The versions are following Semver rules and calculated by looking at the commit history since the last release. The commit title/description may contain a keyword that determine if the update is a major, minor, or patch update:

* `breaking:`: A breaking change that requires a major version update.
* `feature:`: A non-breaking change that requires a minor version update.
* `fix:` (or anything else): A non-breaking change that requires a patch version update.

NOTE: On branches other than `main` the version has a "development" suffix (e.g. `1.0.2-foo.8.5e30d83`).
