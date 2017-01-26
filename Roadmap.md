This document outlines some of the upcoming plans for React Native. Since React Native is a fast-moving project with a large amount of community contribution, this roadmap doesn't include everything that will go into React Native.

The React Native roadmap can be broken down into three key priorities: adding functionality to the core libraries, improving the overall stability of React Native by reducing bugs and breaking changes, and making the developer experience better.

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

## Stability

* Improved packager. Owner: [Christoph Pojer](https://twitter.com/cpojer). ETA: June
    * We are working on further improving stability, reliability and performance of React Native's packager. The precise form this improvement should take is not yet clear. We'll have more exciting news to share in the near future!

## Developer Experience

* Faster app reloads during development. Owners: [cpojer](https://twitter.com/cpojer). ETA: February
    * We'll focus on rewriting packager internals and building updateable bundles so that in development mode only the changed files have to be sent to the device.
* A better "create-react-native-app" workflow. Owners: [Adam Perry](https://github.com/dikaiosune), [martinkonicek](https://twitter.com/martinkonicek). ETA: March
    * The goal is to make it simpler to set up new applications. It should be possible to create a new React Native app without first installing Xcode or Android Studio.

Thanks to all the individuals and companies helping out with the projects on this roadmap!

If you have suggestions for features that you think would be valuable on the roadmap, check out [Product Pains](https://productpains.com/product/react-native), where you can suggest new features and discuss existing proposals, or contact [lacker](https://twitter.com/lacker).
