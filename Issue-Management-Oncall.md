The current oncall is: none. Interested in helping out? Reach out to @hramos.

The oncall rotation is as follows:

- @hramos
- You?

## Oncall Responsibilities

- Triage Issues
- Triage Pull Requests
- Support Releases

_Note:_ Issue Managers do not necessarily have the necessary access level to import PRs, so we might end up splitting this into multiple oncalls. For simplicity's sake, however, I'll focus on describing what I personally do on a day to day basis. -@hramos

## Oncall Playbook

We place a higher priority on pull requests over issues. PRs indicates a higher level of commitment to the project and it is respectful of the author's time to look into each PR as soon as possible.

### Triaging Pull Requests

Take a look at our [Pull Request Priority](https://github.com/facebook/react-native/wiki/Pull-Request-Priority) wiki.

One of the challenges that we face in the React Native project is that the surface area for a PR may be too large for any one person to review. One PR may introduce changes to JavaScript, iOS, and Android. Even focused PRs may have unforeseen performance considerations. We tend to err against importing PRs unless the value add is clear.

We are also working towards slimmening down the core React Native package, therefore we are reluctant to import PRs that may work best as a third party module.

### Triaging Issues

- Go through recently opened issues and add labels to issues that require attention from the original author:
  - No Template: The issue did not follow the new issue template, or they did not fill out some essential fields in the template.
  - Needs More Information: Template or not, the issue as it stands is not actionable. The author may have forgotten to include sample code, or they described an issue that occurs on their app, or they mention it occurs on "the latest version" without specifying which version.
  - Old Version: The author claims the issue occurs on an older version of React Native. If the version they mention is not the [latest](https://github.com/facebook/react-native/releases) (as of the date the issue is created), add this label. Note that people may be using Expo, which lags the stable releases a bit. We still want to add the label -- it is not going to cause the issue to get closed.

Coarsely, issues can be separated into two main groups:

- Regressions
- Unexpected Behavior

This last group describes issues that are not necessarily *bugs* per-se. A good example of this is `zIndex`, which although it works the same in React Native as it does on web, the behavior is not necessarily what people might expect when elements are not siblings of each other ([#698](https://github.com/facebook/react-native/issues/698)).

Most issues will fall into this last bucket. It's unfortunate that the bucket is so coarse, and it does make it harder to prioritize issues that need to be acted on. Ultimately, issues in this bucket will either be the community's responsibility (if you'd like X behavior to change, please code it), or the core team responsibility's (if we don't change how X behaves, people will be endlessly frustrated).

On the other hand, issues that fall into the `Regression` bucket are easier to prioritize. If something used to work, it usually means the behavior is something that can be supported and is not just wishful thinking. It also means the issue may be severely affecting developers.

Therefore, your next task is to surface issues that describe regressions:

- Severity: If the issue describes a behavior that *used to work*, but *broke or changed* in a recent version, please tag them as `Regression`s. 

We do not have a label for issues that do not describe a regression as the category is too broad.

- Lowest priority: go through issues and add secondary labels that might be missing:

Platform labels: `iOS`, `Android`, `Windows`, `tvOS`, `JavaScript`. The bot adds a label to issues based on naive issue title string matching, meaning it misses any context from the body of the issue.


## Contacting the Oncall

TBD

## Week of 04/16/2018

Issues to close:

- No updates in a week, tagged NMI: https://github.com/facebook/react-native/issues?utf8=%E2%9C%93&q=is%3Aissue+is%3Aopen+label%3A%22%3Agrey_question%3ANeeds+More+Information%22+-label%3A%22Core+Team%22+-label%3A%22For+Discussion%22+updated%3A%3C%3D2018-04-09+

- No updates in a week, no template: https://github.com/facebook/react-native/issues?q=is%3Aissue+label%3A%22%3Aclipboard%3ANo+Template%22+-label%3A%22Core+Team%22+-label%3A%22For+Discussion%22+updated%3A%3C%3D2018-04-09+is%3Aopen

- No updates in a week, no repro steps: https://github.com/facebook/react-native/issues?utf8=%E2%9C%93&q=is%3Aissue+label%3A%22%3Aclipboard%3ANeeds+Repro+Steps%22+-label%3A%22Core+Team%22+-label%3A%22For+Discussion%22+updated%3A%3C%3D2018-04-09+is%3Aopen+