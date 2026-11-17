# AnyPS5, patched builds

This is a fork of [AnyPS5](https://github.com/boykopovar/AnyPS5). The `main` branch mirrors upstream. This branch holds only a workflow that builds AnyPS5 for Windows with chosen upstream pull requests merged in, before they reach a release.

## What it does

**Actions → Patched build → Run workflow** takes three inputs:

| Input | Meaning |
|---|---|
| `tag` | Name of the release to publish, such as `vmain-a6606d5-pr19326`. |
| `base` | Upstream branch, tag or full commit SHA to start from. |
| `prs` | Upstream pull request numbers to merge into it, in order, separated by spaces. May be empty. |

It fetches the base from upstream, merges each pull request, builds the relinker and the libraries with the toolchain of the upstream Release workflow, and publishes a release here with `relinker-<tag>.exe` and `prx-windows-<tag>.zip`, the two files of an upstream release that a Windows PC needs. The release notes list the exact commits that were built.

A build with no pull requests becomes the release marked as **Latest**, which is the one a program following this fork downloads. A build with pull requests merged in is published without that mark.

A pull request that does not merge cleanly fails the run. Merging a pull request brings in every upstream commit it is based on, so a base older than that has no effect.

## What it is not

These builds are not reviewed, tested or supported by the AnyPS5 maintainers. The test suite is not run. A pull request is code that upstream has not accepted yet: read it before building it, and do not report problems with these builds upstream without reproducing them on an official release.

AnyPS5 is licensed under the GPL-2.0. The source of each build is the upstream commits named in its release notes.
