A collection of canned responses for issue managers.

**Stack Overflow**:

Use this when a question should be redirected to Stack Overflow. Note that applying the Stack Overflow label should result in the bot doing this for you, but here's the canned response in case that fails:

```
Please use [Stack Overflow](http://stackoverflow.com/questions/tagged/react-native) for this type of question.
```

**Old Version in Environment**:

We commonly get new reports for issues in older versions of React Native. While it is quite possible that the issue may still exist in the latest release, it's the reporter's responsibility to verify the issue has not been fixed before reporting it. Therefore, feel free to post the following whenever a new issue is reported for a release that is not equal or newer to the tag listed at https://github.com/facebook/react-native/releases/latest:

```
It looks like your issue may refer to an older version of React Native. Can you reproduce the issue on the [latest release](https://github.com/facebook/react-native/releases/latest)?
```

Please apply the "Old Version" label as well.

The bot should do comment and label automatically whenever people use `react-native info`, but as of this writing the bot will not trigger if this info is edited into the issue after the fact. Please go ahead and post the above blurb in these cases.

**Old Version, no followup**:

If an issue flagged as being for an old version has not been corrected after 7 days, please close it after commenting with the following:

```
I am closing this issue as the reporter has not yet confirmed the issue exists in the latest release. If you have reproduced this issue in the latest release and are interested in fixing it, please open a new issue with up to date information. Thanks.
```

**Did not use template**:

Use this when a issue does not follow the template.

```
It looks like your issue may be incomplete. Are all the fields required by the [Issue Template](https://raw.githubusercontent.com/facebook/react-native/master/.github/ISSUE_TEMPLATE.md) filled out?
      
If you believe your issue contains all the relevant information, let us know in order to have a maintainer remove the No Template label.
```

The bot should add this comment automatically.

**Did not use template, close**:

Use this when a issue was flagged for not using the template, and still has not been fixed after seven days:

```
It has been a while since a maintainer flagged this issue for not following the [Issue Template](https://raw.githubusercontent.com/facebook/react-native/master/.github/ISSUE_TEMPLATE.md). I will go ahead and close it. If you are interested in fixing this, please submit a new issue will all the relevant information.
```