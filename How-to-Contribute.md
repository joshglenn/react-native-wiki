Thank you for your interest in contributing to React Native! From commenting on and triaging issues, to reviewing and sending PRs, [all contributions are welcome](https://github.com/facebook/react-native/blob/master/CONTRIBUTING.md). In this document, we'll cover the steps to contributing code to React Native.

If you are eager to start contributing code right away, we have a list of [good first issues](https://github.com/facebook/react-native/labels/good%20first%20issue) that contain bugs which have a relatively limited scope. As you gain more experience and demonstrate a commitment to evolving React Native, you may be granted issue management permissions in the main repository.

## Pull Requests

Code-level contributions to React Native generally come in the form of [a pull request](https://help.github.com/en/articles/about-pull-requests). The process of proposing a change to React Native can be summarized as follows:

1. Fork the React Native repository and create your branch from `master`.
2. If you've added code that should be tested, add tests.
3. If you've changed APIs, update the documentation.
4. Ensure the test suite passes, either locally or on CI once you opened a pull request.
5. Make sure your code lints (for example via `yarn lint --fix`).
6. Push the changes to your fork.
7. Create a pull request to the React Native repository.
8. Review and address comments on your pull request.
   1. A bot may comment with suggestions. Generally we ask you to resolve these first before a maintainer will review your code.
9. If you haven't already, complete the Contributor License Agreement ("CLA").

If all goes well, your pull request will be merged. If it is not merged, maintainers will do their best to explain their reasoning.

If this is your first time sending a pull request, we have created a [step-by-step guide to help you get started](https://github.com/facebook/react-native/wiki/Pull-Requests#getting-ready-to-submit-your-first-pull-request). For more detailed information on how pull requests are handled, see the [Pull Requests wiki](https://github.com/facebook/react-native/wiki/Pull-Requests).

## Tests

Tests help us prevent regressions from being introduced to the codebase. The GitHub repository is continuously tested using Circle and Appveyor, the results of which are available through the Checks functionality on [commits](https://github.com/facebook/react-native/commits/master) and pull requests. You can learn more about running and writing tests in the [Tests wiki](https://github.com/facebook/react-native/wiki/Tests).

## Coding Style

We use Prettier to format our JavaScript code. This saves you time and energy as you can let Prettier fix up any formatting issues automatically through its editor integrations, or by manually running `npm run prettier`. We also use a linter to catch styling issues that may exist in your code. You can check the status of your code styling by simply running `npm run lint`.

However, there are still some styles that the linter cannot pick up, notably in Java or Objective-C code.

### Objective-C:

- Space after `@property` declarations
- Brackets on _every_ `if`, on the _same_ line
- `- method`, `@interface`, and `@implementation` brackets on the following line
- _Try_ to keep it around 80 characters line length (sometimes it's just not possible...)
- `*` operator goes with the variable name (e.g. `NSObject *variableName;`)

### Java:

- If a method call spans multiple lines closing bracket is on the same line as the last argument.
- If a method header doesn't fit on one line each argument goes on a separate line.
- 100 character line length

## License

By contributing to React Native, you agree that your contributions will be licensed under the LICENSE file in the root directory of the React Native source tree.
