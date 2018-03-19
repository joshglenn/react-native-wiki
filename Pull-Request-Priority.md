GitHub allows anyone to leave a review on a pull request, regardless of repo commit status. Therefore, we do not import a PR based solely on the fact that it has been reviewed. 

Ultimately, a core team member will need to look at the PR before making the decision to import it or not.

## High priority PRs

These PRs are labeled ["Core Team"](https://github.com/facebook/react-native/pulls?utf8=%E2%9C%93&q=is%3Apr+label%3A%22Core+Team%22). They are usually submitted by core contributors, or have been escalated by core contributors.

- [Review: Approved](https://github.com/facebook/react-native/pulls?utf8=%E2%9C%93&q=is%3Apr+is%3Aopen+label%3A%22Core+Team%22+label%3A%22CLA+Signed%22+sort%3Acreated-desc+NOT+%22WIP%22+in%3Atitle+-label%3A%22Import+Started%22+-label%3A%22Import+Failed%22+review%3Aapproved)
- [Review: None](https://github.com/facebook/react-native/pulls?utf8=%E2%9C%93&q=is%3Apr+is%3Aopen+label%3A%22Core+Team%22+label%3A%22CLA+Signed%22+sort%3Acreated-desc+NOT+%22WIP%22+in%3Atitle+-label%3A%22Import+Started%22+-label%3A%22Import+Failed%22+review%3Anone)
- [All core team PRs regardless of review status](https://github.com/facebook/react-native/pulls?utf8=%E2%9C%93&q=is%3Apr+is%3Aopen+label%3A%22Core+Team%22+label%3A%22CLA+Signed%22+sort%3Acreated-desc+NOT+%22WIP%22+in%3Atitle+-label%3A%22Import+Started%22+-label%3A%22Import+Failed%22)

- [PRs where the import started, but the PR remains open](https://github.com/facebook/react-native/pulls?utf8=%E2%9C%93&q=is%3Apr+is%3Aopen+label%3A%22Core+Team%22+label%3A%22CLA+Signed%22+sort%3Acreated-desc+-label%3A%22Import+Failed%22+label%3A%22Import+Started%22+)
- [PRs where the import failed](https://github.com/facebook/react-native/pulls?utf8=%E2%9C%93&q=is%3Apr+is%3Aopen+label%3A%22Core+Team%22+label%3A%22CLA+Signed%22+sort%3Acreated-desc+label%3A%22Import+Failed%22+)

## Medium priority

These PRs have not been escalated using the "Core Team" label, but are worth following up with at some point for various reasons.

- [PRs where the import started, but the PR remains open](https://github.com/facebook/react-native/pulls?utf8=%E2%9C%93&q=is%3Apr+is%3Aopen+-label%3A%22Core+Team%22+label%3A%22CLA+Signed%22+sort%3Acreated-desc+-label%3A%22Import+Failed%22+label%3A%22Import+Started%22)
- [PRs where the import failed](https://github.com/facebook/react-native/pulls?utf8=%E2%9C%93&q=is%3Apr+is%3Aopen+-label%3A%22Core+Team%22+label%3A%22CLA+Signed%22+sort%3Acreated-desc+label%3A%22Import+Failed%22+)

- [Review: Approved](https://github.com/facebook/react-native/pulls?utf8=%E2%9C%93&q=is%3Apr+is%3Aopen+label%3A%22CLA+Signed%22+sort%3Acreated-desc+-label%3A%22Import+Failed%22+review%3Aapproved+)

- [Fixes a regression](https://github.com/facebook/react-native/pulls?utf8=%E2%9C%93&q=is%3Apr+is%3Aopen+label%3A%22CLA+Signed%22+sort%3Acreated-desc+label%3A%22%3Awarning%3ARegression%22+)

## Low priority

Non-core PRs that have not been imported or reviewed and do not fix a regression are generally looked at last.

- [Review: None](https://github.com/facebook/react-native/pulls?utf8=%E2%9C%93&q=is%3Apr+is%3Aopen+label%3A%22CLA+Signed%22+sort%3Acreated-asc+-label%3A%22Import+Failed%22+-label%3A%22%3Awarning%3ARegression%22+review%3Anone+)

## No priority

- [No CLA - cannot be reviewed](https://github.com/facebook/react-native/pulls?utf8=%E2%9C%93&q=is%3Apr+is%3Aopen+-label%3A%22CLA+Signed%22)

