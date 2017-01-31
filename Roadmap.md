This document outlines some of the upcoming plans for React Native. Since React Native is a fast-moving project with a large amount of community contribution, this roadmap doesn't include everything that will go into React Native.

The React Native roadmap can be broken down into three key priorities: adding functionality to the core libraries, improving the core performance and stability of React Native, and making the developer experience better.

## Core Libraries

* A new standard navigation library. Owners: [skevy](https://twitter.com/skevy), [ericvicenti](https://twitter.com/ericvicenti). ETA: January
    * Right now there are a large number of navigation libraries. We don't think one navigation library will be enough for every use case, but we do think we can make it better. The goal is for this new navigation library to be ideal for apps that handle navigation in JavaScript. Once it is released and stable, we can deprecate Navigator, NavigationExperimental, and ExNavigation.
    * This is in response to the feature request: https://productpains.com/post/react-native/better-navigator-api-and-docs
* Smoother animations. Owners: [ji](https://twitter.com/ji), [janicduplessis](https://twitter.com/janicduplessis). ETA: February
    * There are many improvements here, but a key milestone is when we have the navigation sliding & fading transitions working with the native driver and the backswipe gesture too if that interacts with the native driver in any way.
    * This is in response to the feature request: https://productpains.com/post/react-native/offload-some-animations-from-js-thread-for-better-perf
    * Janic should probably write a blog post once this is all ready.
* A standard navigation library for hybrid apps. Owners: [Leland Richardson](https://twitter.com/intelligibabble). ETA: February
    * A navigation library specifically designed for applications that are part native, part React Native. We are pretty sure the right solution involves a different navigation library. Once this is released and stable, we can deprecate NavigatorIOS.
* Better maps. Owners: [Leland Richardson](https://twitter.com/intelligibabble). ETA: March
    * Since the plan is to make the react-native-maps module the officially recommended maps solution for the React Native community, we need more features to be considered complete. We want iOS support for MapKit, Google Maps, and Mapbox and Android support for Google maps and Mapbox. In particular this should improve quality in China.
* An improved ListView. Owner: [Spencer Ahrens](https://github.com/sahrens). ETA: June
    * There's a lot that can be done here - see Spencer's more detailed notes at https://gist.github.com/sahrens/902d49c6c154cd09fafc52a79503728f . 
    * This is in response to the feature reqest: https://productpains.com/post/react-native/fix-various-listview-issues
* Share C++ code between Android and iOS bridges. Owner [Marc Horowitz](https://github.com/mhorowitz). ETA: March/April
    * Building the C++ bridge on top of a common code base reduces code duplication, makes the two platforms more consistent, makes it faster to iterate on the lower layers of the bridge, and enables efficient use of cross-platform C++ modules.
    * For code using documented React Native interfaces, this should be an invisible change.

## Core Performance

* Improved packager. Owner: [Christoph Pojer](https://twitter.com/cpojer). ETA: June
    * We are working on further improving stability, reliability and performance of React Native's packager. The precise form this improvement should take is not yet clear. We'll have more exciting news to share in the near future!
* Turn on Nodes by default for new React Native apps. Owner: [Aaron Chiu](https://github.com/AaaChiuuu). ETA: June
    * Nodes is a new mechanism for layout that should improve performance and fix several longstanding dysfunctions.
    * It's currently available but has to be explicitly enabled. We need it to be compatible with existing features before flipping it to the default.
* Significantly improve performance, focusing on Android. Owner: [Aaron Chiu](https://github.com/AaaChiuuu). ETA: June
    * There's a number of performance improvements so this breaks down into a lot of smaller issues.

## Developer Experience

* Faster app reloads during development. Owners: [cpojer](https://twitter.com/cpojer). ETA: February
    * We'll focus on rewriting packager internals and building updateable bundles so that in development mode only the changed files have to be sent to the device.
* Better templates for creating new apps. Owner: [Martin Konicek](https://twitter.com/martinkonicek). ETA: March
    * Xcode, for example, lets you create a new app with stack or tab navigation via UI. It should be easy to do this in React Native too.
* A better "create-react-native-app" workflow. Owners: [Adam Perry](https://github.com/dikaiosune), [martinkonicek](https://twitter.com/martinkonicek). ETA: March
    * The goal is to make it simpler to set up new applications. It should be possible to create a new React Native app without first installing Xcode or Android Studio.
* A new React Native tutorial. Owner: [Hector Ramos](https://twitter.com/hectorramos?lang=en). ETA: April
    * Currently there is a tutorial but it is doing double duty as reference material because it doesn't really read linearly. The idea of this new tutorial is to take you through building a reasonable sample app.

Thanks to all the individuals and companies helping out with the projects on this roadmap!

If you have suggestions for features that you think would be valuable on the roadmap, check out [Product Pains](https://productpains.com/product/react-native), where you can suggest new features and discuss existing proposals, or contact [lacker](https://twitter.com/lacker).
