GitHub issues are our main channel for handling bug reports that affect open source consumers. 

The core React Native repository has a large surface area, with support for the two most popular mobile platforms: Android and iOS. Our users come from a variety of backgrounds, experience levels and platforms like Android, iOS and web. Each bug report we get can be wildly different, from small rendering bugs, slight discrepancies between platforms, or scary showstoppers that crash the app. Troubleshooting and working on the proper fix for a bug can sometimes require deep understanding of React Native's internals as well as intimate knowledge of the mobile platforms, sometimes a fix might be a trivial one line change. 

The React Native team at Facebook may split their time between supporting internal customers and work that improves React Native's architecture. External contributors tend to have a main job that occupies most of their time. That is to say, the people who can troubleshoot and work on a fix may have limited time to look at each issue. As a result, we have come up with a process to help us triage issues.

The main thing to keep in mind is that we are, at this time, only accepting bug reports through the https://github.com/facebook/react-native issue tracker. If you have a proposal for a new feature or enhancement, or you would like to discuss some aspect of how React Native is architected, we have set up a separate repository at https://github.com/react-native-community/discussions-and-proposals to help with that.

Now that you have a better understanding of how we approach the GitHub repository, let's dive into what you can do to help triage GitHub issues in the https://github.com/facebook/react-native repository.

## Triaging Issues

First, [filter out any issues that already contain one of the resolution labels](https://github.com/facebook/react-native/issues?utf8=%E2%9C%93&q=is%3Aissue+is%3Aopen+label%3A%22Bug+Report%22+-label%3A%22Resolution%3A+Needs+More+Information%22+-label%3A%22Resolution%3A+Needs+Repro%22+-label%3A%22Resolution%3A+Old+Version%22+-label%3A%22Resolution%3A+No+Template%22+-label%3A%22Resolution%3A+Missing+Environment+Info%22+-label%3A%22Resolution%3A+For+Stack+Overflow%22).  Then, figure out if the issue contains all the information needed to troubleshoot. This includes a **clear description** of the problem, information about the development **environment** (including the version of React Native being used), and a list of **steps to reproduce** the issue. If any of these are missing, *politely* ask the issue author to update their issue with the necessary information, and add any relevant resolution labels to let others know the issue has been looked at. We aim to always be friendly and helpful and expect the same from every member of our community.

### Non-conforming Issues

Sometimes, people may clear out the “Bug Report” template, adding in some freeform text instead. Whenever this happens, you may add a “No Template” resolution label. This will tell one of our bots that it's OK to close the issue. In some cases, the author may have a good reason for omitting the template. Use your judgement to determine if the issue should remain open.

### Requests for Help

In other cases, a question or request for help may be submitted as a bug report. You can add the “For Stack Overflow” label to these issues. A bot will eventually close out the issue and point the author to ask their question on Stack Overflow instead. It's fine to do this even if there's a number of comments on the issue, as it's OK if the involved parties want to continue their conversation thread in the closed issue.

### Documentation Bugs

If there's something wrong in the docs, ask the author to post their issue to https://github.com/facebook/react-native-website instead, or, even better, ask them to send a pull request with a fix to the website repository.

### Improving an Issue

If the issue contains all the necessary information, take a moment to consider if the issue can still be improved in some way. Is the formatting alright? You may lightly edit the issue to improve readability as needed. If the issue contains an unformatted block of code, surround it with three back ticks (```) to convert it into a markdown code block. Are there any labels you can add to help categorize it better? If the issue only affects Android apps, you may add a “Platform: Android” label. Perhaps the issue only manifests itself when developing on Windows, in which case you might add the “Platform: Windows” label. We have a long list of [labels](http://github.com/facebook/react-native/issues/labels), please take a look and see if anything might apply!

### Handling Duplicates

As you work through these issues, you will start to get a better understanding of the type of problems that get reported. You may even start noticing the same issue gets reported. In these cases, you can close the issue and add a comment that says “Duplicate of #issue”. By following this convention, GitHub will automatically mark the issue as a duplicate.

### Assessing Impact

Next up, we need to determine how severe the issue is.

* Is this a potential release blocker?
  These issues should be addressed within the next week or two, as they may prevent release coordinators from cutting a clean release candidate. Issues that might be labeled as such could be regressions that break one of our pre-commit tests. Avoid flagging an issue as a release blocker if it has been around for some time (if the issue is already present in one or more releases, it cannot be a RC blocker by definition).
* Does this cause the app to crash? 
  These are issues that cause a React Native to crash unexpectedly. These may lead to a poor user experience if not caught early. 
* Is this a bug? 
  Describes something that is not working as expected. It'd be nice to get it fixed at some point, but it's not serious enough to block the release train. Even if the issue causes a crash, if there's a reasonable workaround available, it can be classified as a regular bug.
* Is this a good first issue?
  These are issues that do not require a deep understanding and familiarity with the repo. GitHub will surface these issues to folks interested in becoming contributors. Keep in mind that issues labeled this way may not end up getting fixed right away.

**Appendix: Labels**

Most of [our labels](https://github.com/facebook/react-native/issues/labels) have a prefix that provides a hint of their purpose. You'll notice right away there's two types of labels that dominate the list: [API](https://github.com/facebook/react-native/labels?utf8=%E2%9C%93&q=API%3A), and Component. These generally denote issues and pull requests related to an API or Component. It helps us understand, at a glance, which components are in dire need of documentation or support. These labels are added automatically by one of our bots, but feel free to adjust them if the bot mis-attributes an issue.

* The `p:` class of labels denote a company with whom with maintain some sort of [relationship](https://github.com/facebook/react-native/blob/master/ECOSYSTEM.md). These include Microsoft and Expo, for example. These are also added automatically by our tooling, based on the issue author.
* The `DX:` class of labels denote areas that deal with the developer experience. Use these for issues that negatively impact people who use React Native.
* The `Tool:` class of labels denote tooling. CocoaPods, Buck...
* The `Resolution:` labels help us communicate the status of an issue. Does it need more information? What needs to be done before it can move forward?
* The `Type:` labels are added by a bot, based on the changelog field in a pull request.
* The `PR:` labels are used to help us assess the state of a pull request.
* The `Platform:` labels help us identify which development platform or target OS is affected by the issue.

When unsure of the meaning of a particular label, go to https://github.com/facebook/react-native/labels and look at the description field. We'll do our best to properly document these.

**Appendix: Bots**

* **@react-native-bot**: The React Native bot is a tool that helps us automate several processes described in this wiki.
* **@pull-bot**: The Pull Bot automates several aspects of the pull request review process, such as making sure test plans and changelogs are used. It is based on Danger, and it is configured through the [`dangerfile`](https://github.com/facebook/react-native/blob/master/bots/dangerfile.js).
* **@analysis-bot**: Another helpful process that aids in pull request reviews, focusing mostly on lint and Flow checks. It is configured to run as part of the CI processes whenever a commit is added to a pull request.
