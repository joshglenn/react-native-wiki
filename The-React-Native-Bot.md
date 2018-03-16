If you've submitted an issue or opened a pull request, you probably already know about [@react-native-bot](https://github.com/react-native-bot). This bot does its best to get issues and PRs into a good shape. If you're wondering how the bot accomplishes this, read on.

# Issue Management

## Labeling issues based on keywords in the title

Issues with "Android" in the title will get labeled as `"Android"` issues. Pretty straightforward. It may rarely result in false positives (i.e. an iOS issue with the title "X works fine on Android, but not on iOS"), but that's OK.

## Flagging issues that lack a template

All new issues must follow the [ISSUE_TEMPLATE](https://github.com/facebook/react-native/blob/master/.github/ISSUE_TEMPLATE.md). If the template is not followed, the bot will add a `"No Template 📋"` label and let the author know by leaving a comment.

The way the bot checks for the template is pretty naive: it looks for the string "Environment" within the body of the issue. That's one of the required fields in the template, and its omission is a good indicator the author failed to fill out the issue. After all, this section is required for the next task. 

## Flagging issues that have not been reproduced on the latest release

We only want to track issues on the latest stable release. Ideally, every contributor would ensure their issue can be reproduced on master, but that takes a bit more effort than people are willing to put in. In any case, the bot will look for the string, "react-native: major.minor.patch => major.minor.patch" and it will flag any issues where the major.minor does not match the [latest release](https://github.com/facebook/react-native/releases). It will do so by adding a `"Old Version 🕐"` label to the issue.

As it happens, if the author did indeed check against master, or perhaps an RC, the bot will incorrectly flag the issue. Feel free to send a PR if you're interested in fixing this! It's a `"Good first issue"` to tackle.

## Closing issues that are questions for Stack Overflow

We use GitHub issues strictly for tracking bug reports. Sometimes we'll get an issue that is really something that would be best asked on Stack Overflow. It could be either a request for code-level help, or a general React question. We leave it up to maintainers to figure out when an issue meets the criteria, in which case they'd add a `"For Stack Overflow :question:"` label.

This is where the bot comes in. If it finds an issue with a `"For Stack Overflow :question:"` label, it will automatically close the issue and leave a comment asking the author to post their question over there.

# Pull Request Management

## Labeling PRs based on keywords in the title

PRs with "iOS" in the title will get labeled as `"iOS :iphone:"` issues. Pretty straightforward. Just like with Issues.

# How?

The bot runs every five minutes. In most cases, it will only check issues or PRs opened or updated within the last day or so. You can learn more by reading through the [source code](https://github.com/hramos/iceboxer).