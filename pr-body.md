# PR Explanation

Hello from the Developer Ecosystem team at New Relic! This PR contains a GitHub actions workflow which runs [Repolinter](https://github.com/todogroup/repolinter), an automated tool to help us find and fix inconsistencies in our public repositories. This PR registers a GitHub Actions workflow (`nr1_lib_deprecations.yml`) running [repolinter-action](https://github.com/newrelic/repolinter-action). The goal of this workflow is to validate that your New Relic One application is making use of the most current `nr1` JS libraries by reporting any deprecation warnings or errors.

## Repolinter Action does

* Scans the repository for nr1 library deprecation issues using Repolinter.
* The issues this workflow scans for are determined by the ruleset specified by `with.config-url`: this ruleset will be maintained by the Open Source and Developer Advocacy team and will not change frequently.
* Runs only on push to the default branch, ignoring PRs and other events.
* If any policy issues are found, this workflow will open a GitHub issue titled "NR1 Lib Deprecations" and with the `repolinter` label. This issue will contain detailed information on which policies generated errors and what changes are suggested.
* As policy issues are resolved, this workflow will update the open issue to reflect the changes. If all policy issues are resolved, the issue will automatically be closed.

This workflow is designed to cause the least amount of friction as possible:

* This workflow will only run on push, and as a result will not participate in status checks for PRs. Furthermore, this workflow will always exit with a passing status unless a fatal internal error occurs.
* It is up to your team to backlog the items found by this tool appropriately.
* This workflow will only notify you when an issue is created. In other words, you will only be notified when new problems occur, but not when existing problems change.

## What you should do

* Review this PR and workflow. Make sure that the correct base branch is selected.
* If this workflow conflicts with your team's infrastructure, let us know in #help-opensource! We're happy to work with individual project needs.
* If the PR looks good, merge the PR and check to see if the repolinter-action runs successfully in the actions console. You can remove the branch created by this PR as it is no longer needed.
* The action may open a GitHub issue on this repository (it will have the `repolinter` label). If an issue is opened, look it over and make sure all the problems seem correct. Shoot us a ping in #help-opensource if anything looks suspicious.
* In the future, this workflow may open issues as our NR1 library deprecation checks are updated. Keep an eye on the GitHub issues for these updates (it may help to watch the repository).

If you have feedback, please let us know in #help-opensource. Thanks!