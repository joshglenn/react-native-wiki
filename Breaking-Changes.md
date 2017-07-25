This is a complete list of breaking changes in each release of React Native, compiled as commits land. This way we can get enough information from owners right when the change is still fresh in their memory.

This document serves two goals:
- **Easier upgrades**. The contents of this document will be printed by `react-native upgrade` so that when people upgrade their app to a new version of React Native they have clear instructions on how to modify their code.
- **Tracking** the number of breaking changes over time, understanding the motivation behind each of them and eventually having an idea how to reduce the amount of breaking changes.


Changes that are likely to be present in the next release are listed under `master`.

When adding a new breaking change, follow this template:
```
### New breaking change here

- **Who does this affect**:
- **How to migrate**:
- **Why make this breaking change**: 
- **Severity (number of people affected x effort)**:
```


# master

```
### D5484225 createClass codemod
This is a codemod that replaces `React.createClass` with an ES6 class when possible, and falls back to the separate `create-react-class` npm module when not possible. Flow and Jest tests passed.
- **Who does this affect**: It should not introduce breaking changes, but as it touched a lot of files we are making a note of it here.
- **How to migrate**: No migration necessary. If you're interested in doing this on your own projects, take a look at [react-codemod](https://github.com/reactjs/react-codemod#explanation-of-the-new-es2015-class-transform-with-property-initializers).
- **Why make this breaking change**: This is part of the move to React 16.
- **Severity (number of people affected x effort)**:
```

### D5078004, D5137181 [ReactNative] Update okhttp3 to 3.6.0 - *@emilsj in FB*
- **Who does this affect**: The largest change is that websockets moved into the main package and saw some API changes.
- **How to migrate**:
- **Why make this breaking change**: 
- **Severity (number of people affected x effort)**:

### D4611211 [ReactNative][Android][breaking] move NativeModule initialization off UI thread - @AaaChiuuu
*@aaronechiu in FB*
- **Who does this affect**: Native modules which need initialization on the UI thread.
- **How to migrate**: Move the UI thread specific to be run on the first time onHostResume() is called.
- **Why make this breaking change**: Potentially breaks threading requirements.
- **Severity (number of people affected x effort)**: Low


### Flow Config Change ([b0bdbe](https://github.com/facebook/react-native/commit/b0bdbeb5c3b5c1dbea57ce81b9f43bd5845dc409)) - @skevy
- **Who does this affect**: Any app which uses flow-typed code
- **How to migrate**: Update the `.flowconfig` file inside your project with the following change:
https://github.com/facebook/react-native/commit/b0bdbeb5c3b5c1dbea57ce81b9f43bd5845dc409
- **Why make this breaking change**: Adds a new `$FlowExpectedError` which is useful for test cases that are meant to throw
- **Severity (number of people affected x effort)**: Medium

### D4456312 (not landed yet)

- **Who does this affect**: Product developers
- **How to migrate**: ? Fix should be quite straightforward. Just find elements affected and add flexGrow property to elements that aren't growing as expected.
- **Why make this breaking change**: Fixes a bug in Yoga that allowed grandchild of an element to flex itself to the maximum size even though its direct parent didn't use flexGrow. You can see the difference between them here:
http://jsfiddle.net/y11txxv9/279 and http://jsfiddle.net/y11txxv9/278. In Yoga the first scenario (http://jsfiddle.net/y11txxv9/279/) doesn't behave correctly, resulting in the same layout as in second scenario.
You can see the difference between them here:
- **Severity (number of people affected x effort)**: Medium

### D4398956: Breaking - (Re)moving `JSBundleLoader.getSourceUrl()`- @amnn
*@ashokmenon in FB*

- **Who does this affect**: People using any of the following API's to access the Source URL of their React Native bundle:
  - `JSBundleLoader.getSourceUrl()`
  - `ReactInstanceManager.getSourceUrl()`
  - `ReactInstanceManager.getJSBundleFile()`
- **How to migrate**: Instead, refer to the source of truth for this information, which is at `CatalystInstance.getSourceURL()`, or the return value of `JSBundleLoader.loadScript()`.
- **Why make this breaking change**: It is possible to implement loaders that do not know the exact source URL they will load until after it has already been loaded. E.g. A loader that tries to multiple sources until one succeeds. To allow us to implement such loaders, we are removing the assumption that the source URL is statically determinable.
- **Severity (number of people affected x effort)**: Very few people should be affected, and migration effort is low.

### D4157971 (not landed yet, need changes to product code at fb) - @emilsjolander

- **Who does this affect**: Product developers (Android)
- **How to migrate**: ? Fill this in once/if the diff lands.
- **Why make this breaking change**: Fixes wrong behavior - makes this behave the same as on the web. Repro in https://github.com/facebook/react-native/issues/10603
- **Severity (number of people affected x effort)**: ?

# 0.44

### iOS: Support withCredentials flag in XHRs ([454ab8](https://github.com/facebook/react-native/commit/454ab8fc238da16f9c3986d9a64ea8e716ac0bac))

- **Who does this affect**: iOS product developers who rely on XHR to send cookies by default
- **How to migrate**: Configure XHR requests to send cookies by providing the `withCredentials` argument to `sendRequest`
- **Why make this breaking change**: Enables consistency with the default behavior of XHR on web for cross-site requests
- **Severity (number of people affected x effort)**: Low


### iOS: Remove MapView ([48f30e](https://github.com/facebook/react-native/commit/48f30eca7e3d4c239501de515a7cc35615ed6bd1)) - mkonicek
- **Who does this affect**: Product developers (iOS)
- **How to migrate**: Use https://github.com/airbnb/react-native-maps
- **Why make this breaking change**: MapView has been deprecated for a long time. airbnb/react-native-maps is better and works on both platforms.
- **Severity (number of people affected x effort)**: Medium

# 0.43

### Android: Only call onLayout when layout has actually changed ([15429e](https://github.com/facebook/react-native/commit/15429e333f8fd80c4778f222058dbb16278cf625)) - @astreet

- **Who does this affect**: Product developers (Android)
- **How to migrate**: Depends on how you use `onLayout`. It will only be called when the layout actually changes.
- **Why make this breaking change**: Fixes wrong behavior - previously `onLayout` was called to often which was bad for perf.
- **Severity (number of people affected x effort)**: Medium

# 0.41

### Android - ReactNativeHost getUseDeveloperSupport to public ([f3c815](https://github.com/facebook/react-native/commit/f3c8158773edf418833ff0032414433edbc6cd62)) - @jpshelley

- **Who does this affect**: Product developers
- **How to migrate**: Change `protected boolean getUseDeveloperSupport() {` to `public boolean getUseDeveloperSupport() {` in your `MainApplication.java` file.
- **Why make this breaking change**: This allows `ReactNativeHost` to be more easily used outside of the `ReactActivity` and `ReactActivityDelegate` ecosystem. (A `ReactFragment` would be a good example).
- **Severity (number of people affected x effort)**: Medium

# 0.40

### Kill deprecated `require('image!...')`: ([ca58e0](https://github.com/facebook/react-native/commit/ca58e0af82797042fabad3873478bc4a9feb7281)) - @davidaurelio 

- **Who does this affect**: Product developers
- **How to migrate**: Use `<Image source={require('./icon.png')} />`. See http://facebook.github.io/react-native/docs/images.html for more info. In rare cases when you need to directly access native images present in your hybrid app, use `nativeImageSource`.
- **Why make this breaking change**: The API has been deprecated for a very long time and the alternative is much better.
- **Severity (number of people affected x effort)**: Low (hopefully everyone migrated a long time 

### Namespace all header imports to `<React/...>` ([e1577d](https://github.com/facebook/react-native/commit/e1577df1fd70049ce7f288f91f6e2b18d512ff4d)) - @javache

- **Who does this affect**: iOS library authors who have custom integrations with React Native
- **How to migrate**: If you encounter build errors replace `#import "RCT*"` with `#import <React/...>`. See the commit for more details.
- **Why make this breaking change**: This improves interoperability with FB's internal build system and makes it easier to use React Native in a mixed hybrid environment
- **Severity (number of people affected x effort)**: Very high

In third-party native code, instead of

    #import "RCTBridge.h"

use a name-spaced system import

    #import <React/RCTBridge.h>

### Change the `JSCExecutor::callFunctionSync` C++ template ([bd524b](https://github.com/facebook/react-native/commit/bd524bd6e857ada8ec827d65a163d8838e96640b)) - Lukas Piatkowski

- **Who does this affect**: Library authors who call `callFunctionSync` from Obj-C, or from Java via JNI.
- **How to migrate**: Check all the places where you call the native `callFunctionSync`.
- **Why make this breaking change**: Fixes a bug.
- **Severity (number of people affected x effort)**: Very low


# 0.39

### Move to new C-based implementation of css-layout on Android ([d63ba4](https://github.com/facebook/react-native/commit/d63ba47b59e3261403800c1f741d979a089efb48)) - @astreet

- **Who does this affect**: Product developers, Android
- **How to migrate**: Previously, developers had to put `flex: 1` in many places it didn't belong in order to work around a bug in css-layout. Now `flex: 1` is treated properly and, unfortunately, this means that your layout may no longer look correct. Specifically, you may see that your layout looks collapsed, or children don't render. The fix is to simply remove `flex: 1` from those containers.
- **Why make this breaking change**: The C-based implementation fixes bugs in layout, the behavior is closer to web. The C-based implementation is also faster.
- **Severity (number of people affected x effort)**: Low


### Fix inconsistency with fractional TextInput padding ([aa8540](https://github.com/facebook/react-native/commit/aa85408f568ae9776fef99dcae317def0a07139a)) - @rigdern

- **Who does this affect**: Product developers
- **How to migrate**: This bugfix can cause padding on TextInputs to be off by one pixel compared to the last version but it most cases you don't need to change your code.
- **Why make this breaking change**: Fixes a bug.
- **Severity (number of people affected x effort)**: Low

### Android: Disable debug menu when Monkey is running ([9a8b5d](https://github.com/facebook/react-native/commit/9a8b5d9f4f860f16d0845d537f80bfd2f515ee93)) - @ridgern

- **Who does this affect**: Integration/End-To-End Testers, Android
- **How to migrate**: Use another mechanism if your e2e test requires the dev menu.
- **Severity (number of people affected x effort)**: Low


# 0.38

###  NativeModules IOS: Remove `customDirectEventType` ([aa4428c](https://github.com/facebook/react-native/commit/aa4428cd132bb0d0dbc950b66d3b5f2a3c5b9322)) - @javache
- **Who does this affect**: People writing 3rd-party modules on iOS
- **How to migrate**: Declare properties of type `RCTDirectEventBlock` instead
- **Why make this breaking change**: The new API is better and we don't want to keep the old one around.
- **Severity (number of people affected x effort)**: Low


# 0.37

### Remove deprecated APIs and modules ([fa5ad8](https://github.com/facebook/react-native/commit/fa5ad85252be9e5e5a8f04d705463e7ba4cb85e3)) - @satya164

- **Who does this affect**: Product developers
- **How to migrate**: Import the following modules instead. The API of the new ones should be the same of very similar: `AppStateIOS` -> `AppState`, `ActivityIndicatorIOS` -> `ActivityIndicator`, `IntentAndroid` & `LinkingIOS` -> `Linking`, `SliderIOS` -> `Slider`, `SwitchAndroid` & `SwitchIOS` -> `Switch`
- **Why make this breaking change**: These old APIs were designed a long time ago when we didn't think about Android and platform parity at all. We do now :)
- **Severity (number of people affected x effort)**: Medium


### Remove callback support from Clipboard and NetInfo ([fa5ad8](https://github.com/facebook/react-native/commit/fa5ad85252be9e5e5a8f04d705463e7ba4cb85e3)) - @satya164

- **Who does this affect**: Product developers
- **How to migrate**: Don't pass a callback to `Clipboard.getString()` and `NetInfo.isConnectionExpensive()`. Both methods return a `Promise` now, use the `Promise`.
- **Why make this breaking change**: A long time ago we didn't a way to return Promises from native to JS so we used to use callbacks. Now Promises should be used everywhere.
- **Severity (number of people affected x effort)**: Low


# 0.36

### Default scrollview to flexShrink to allow views below it ([c43a3f](https://github.com/facebook/react-native/commit/c43a3f5d8412eb0dfe894a192f15efa9c41ab318)) - @emilsjolander.
- **Why make this breaking change**: Some layouts were broken due to having views below the ScrollView. Not sure if breaking change, we only know of product code this fixed, not broke.


### Fix unconstraint sizing in main axis ([0a9b6b](https://github.com/facebook/react-native/commit/0a9b6bedb312eba22c5bc11498b1cc41363e5f27)) - @emilsjolander

- **Who does this affect**: Product developers
- **How to migrate**: Most of your layouts will continue to function as before however some of them might not. Typically this is due to having a `flex: 1` which after this change may collapse your component to take zero size due to the implicit `flexBasis: 0` now being correctly treated. Removing the bad `flex: 1` style or changing it to `flexGrow: 1` should solve most if not all layout issues your see after this change.
- **Why make this breaking change**: The previous behavior was wrong.
- **Severity (number of people affected x effort)**: Medium


### Fix modal resizing on keyboard show ([404b7c](https://github.com/facebook/react-native/commit/404b7cc069471cc8e0277d398751305665f0d3e1)) - @andreicoman11

- **Who does this affect**: Product developers, Android
- **How to migrate**: No need to change your code. Modals will now resize on keyboard show by default, since that is the default correct Android behavior.
- **Why make this breaking change**: Resizing is the correct behavior on Android.
- **Severity (number of people affected x effort)**: Low