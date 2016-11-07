This document outlines some of the upcoming plans for React Native. Since React Native is a fast-moving project with a large amount of community contribution, this roadmap doesn't include everything that will go into React Native.

The React Native roadmap can be broken down into three key priorities: adding functionality to the core libraries, improving the overall stability of React Native by reducing bugs and breaking changes, and making the developer experience better.

## Core Libraries

* A new standard navigation library. Owners: skevy, eric vicenti. ETA: November
    * Right now there are a large number of navigation libraries. We don't think one navigation library will be enough for every use case, but we do think we can make it better. The goal is for this new navigation library to be ideal for apps that handle navigation in JavaScript. Once it is released and stable, we can deprecate Navigator, NavigationExperimental, and ExNavigation.
    * This is in response to the feature request: https://productpains.com/post/react-native/better-navigator-api-and-docs
* Faster animation. Owners: ide, janic. ETA: December
    * There are many improvements here, but a key milestone is when we have the navigation sliding & fading transitions working with the native driver and the backswipe gesture too if that interacts with the native driver in any way.
    * This is in response to the feature request: https://productpains.com/post/react-native/offload-some-animations-from-js-thread-for-better-perf
* Orientation. Owners: mehdi. ETA: January
    * A better library for letting developers control orientation in an app. This has been a common area of feedback and we think we can improve the experience here.
* Complete Apple TV support. Owners: doug lowder. ETA: January
    * The focus engine support needed for Apple TV to work is still in review.  In addition, we still need to handle test automation for the Apple TV focus engine support, making other projects in the Examples directory (besides UIExplorer) work on Apple TV, generation of new Apple TV projects in react-native-cli, and making the packager (and Javascript layer) aware if a bundle is intended to run on Apple TV.
* A standard navigation library for hybrid apps. Owners: leland. ETA: February
    * A navigation library specifically designed for applications that are part native, part React Native. We are pretty sure the right solution involves a different navigation library. Once this is released and stable, we can deprecate NavigatorIOS.
* Better maps. Owners: leland. ETA: March
    * Since the plan is to make the react-native-maps module the officially recommended maps solution for the React Native community, we need more features to be considered complete. We want iOS support for MapKit, Google Maps, and Mapbox and Android support for Google maps and Mapbox. In particular this should improve quality in China.

## Stability

* Deprecating the existing MapView. Owners: martink. ETA: November
    * In practice, react-native-maps is a better mapping library. We haven't made a regular practice of deprecating things, so there's some work needed to make it a clean experience, like supporting an intermediate warning period, and possibly helping people upgrade with codemods or spinning out the existing MapView into a separate library for people who can't upgrade. Once we develop a clean deprecation process we'll apply it to other components as well.
* Improved sourcemaps. Owners: ovidiu iepure. ETA: December
    * There are a set of issues with sourcemaps that we intend to fix. Some notable ones are setting break points within JSX, and fixing the off-by-x errors in production maps. There is other work to fix crashes and generally make sourcemaps work better.

## Developer Experience

* Templates for react-native init. Owners: martink. ETA: January
    * The goal is to make it simpler to set up new applications, by providing templates for a few common use cases. In particular, a template is very useful for setting up the root navigation flow, so for tabbed apps or for apps that use a card stack as the root view, templates should make that noticeably easier.
* Flowtyping the core components. Owners: tim yung, alex kotliarsky. ETA: January
    * Making the most common components come with Flow types, for a better typechecking experience. This should also make it easier to reduce breaking changes. Flow already comes with React Native, so this is a logical step to further improve the experience.
* Faster app reloads during development. Owners: Christoph Pojer. ETA: February
    * We'll focus on rewriting packager internals and building updateable bundles so that in development mode only the changed files have to be sent to the device.

Thanks to all the individuals and companies - Facebook, Exponent, Airbnb, and Salesforce - helping out with the projects on this roadmap!

If you have suggestions for features that you think would be valuable on the roadmap, check out [Product Pains](https://productpains.com/product/react-native), where you can suggest new features and discuss existing proposals.
