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

## Closing issues that need more information

If an issue has not been updated in over 7 days and it has a `"No Template :clipboard:"` label, the bot will close the issue and leave a comment.

Ideally, the bot would check if the template has been used whenever the issue is edited, but we're not there yet. So we rely on maintainers to manually remove the label for the time being.

## Exceptions

The bot will avoid closing issues that are marked as `"Core Team"` or `"For Discussion"`. This provides us with a escape valve whenever a maintainer notices an issue that may deviate from the template for a good reason (i.e. a discussion that is worth keeping on the repo), or when the issue really needs further attention from the core contributors team.

# Pull Request Management

## Labeling PRs based on keywords in the title

Just like with Issues, PRs with "iOS" in the title will get labeled as `"iOS :iphone:"` issues. Pretty straightforward...

## Labeling PRs based on release notes

...but we're not done yet. The [PULL_REQUEST_TEMPLATE](https://github.com/facebook/react-native/blob/master/.github/PULL_REQUEST_TEMPLATE.md) asks contributors to write their own release notes. The bot uses these to figure out additional, useful labels such as `"Bug Fix :bug:"` or `"Breaking Change :boom:"`, or even `"Android"` if the title did not already mention it.

## Flagging PRs that lack release notes

Of course, if no release notes are present, the bot cannot properly tag a PR. In these cases, the bot will politely nag the contributor to add these to their PR.

## Flagging PRs that lack test plans

Oh no. We can't permit a PR to be landed without a sane test plan. These make the bot quite unhappy, and the bot will add a "No Test Plan :clipboard:" label. That will show 'em.

## Flagging large PRs

I mean... I guess it's OK. Thank you for the pretty significant contribution. We'll try to review it... as soon as we can... maybe we can get some smaller PRs in first?

Seriously, we don't want to dissuade large contributions, and in many cases, it's OK for a PR to touch a large number of lines. The bot just wants to let you know that, well, your PR is quite big and it may take longer to review.

## Flagging PRs by core contributors

If you've sent some quality PRs our way or are actively involved in the project, the bot may flag your PR as `"Core Team"`. Ideally, maintainers look at these PRs first and foremost. Look at this as an incentive for actively involved contributors ❤️ .

# How does it work?

The bot runs every five minutes. In most cases, it will only check issues or PRs opened or updated within the last day or so. You can learn more by reading through the [source code](https://github.com/hramos/iceboxer).