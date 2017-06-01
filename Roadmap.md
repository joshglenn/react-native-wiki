This document outlines some of the upcoming plans for React Native. Since React Native is a fast-moving project with a large amount of community contribution, this roadmap doesn't include everything that will go into React Native.

The React Native roadmap can be broken down into three key priorities: adding functionality to the core libraries, improving the core performance and stability of React Native, and making the developer experience better.

## Core Performance

* Improved packager. Owner: [Christoph Pojer](https://twitter.com/cpojer). ETA: June
    * We are working on further improving stability, reliability and performance of React Native's packager. The precise form this improvement should take is not yet clear. We'll have more exciting news to share in the near future!
* Turn on Nodes by default for new React Native apps. Owner: [Aaron Chiu](https://github.com/AaaChiuuu). ETA: June
    * Nodes is a new mechanism for layout that should improve performance and fix several longstanding dysfunctions.
    * It's currently available but has to be explicitly enabled. We need it to be compatible with existing features before flipping it to the default.
* Significantly improve performance, focusing on Android. Owner: [Aaron Chiu](https://github.com/AaaChiuuu). ETA: June
    * There's a number of performance improvements so this breaks down into a lot of smaller issues.
* Share C++ code between Android and iOS bridges. Owner [Marc Horowitz](https://github.com/mhorowitz). ETA: April
    * Building the C++ bridge on top of a common code base reduces code duplication, makes the two platforms more consistent, makes it faster to iterate on the lower layers of the bridge, and enables efficient use of cross-platform C++ modules.
    * For code using documented React Native interfaces, this should be an invisible change.

## Developer Experience

* Faster app reloads during development. Owners: [cpojer](https://twitter.com/cpojer). ETA: March
    * We'll focus on rewriting packager internals and building updatable bundles so that in development mode only the changed files have to be sent to the device.
* Better templates for creating new apps. Owner: [Héctor Ramos](https://twitter.com/hectorramos). ETA: June
    * Xcode, for example, lets you create a new app with stack or tab navigation via UI. It should be easy to do this in React Native too.
    * [Martin Konicek](https://twitter.com/martinkonicek) has already implemented this and it is now available, but we have yet to write documentation. Héctor is working on some default templates.
* A new React Native tutorial. Owner: [Héctor Ramos](https://twitter.com/hectorramos). ETA: June
    * Currently there is a tutorial but it is doing double duty as reference material because it doesn't really read linearly. The idea of this new tutorial is to take you through building a reasonable sample app.

Thanks to all the individuals and companies helping out with the projects on this roadmap!

If you have suggestions for features that you think would be valuable on the roadmap, check out [Canny](https://react-native.canny.io/feature-requests/), where you can suggest new features and discuss existing proposals, or contact [@hectorramos](https://twitter.com/hectorramos).

