This is a **complete** list of breaking changes in each release of React Native, compiled **as commits land**. This way we can get enough information from owners right when the change is still fresh in their memory.

This document serves two goals:
- **Easier upgrades for people**. The contents of this document are printed by `react-native upgrade` so that when people upgrade their app to a new version of React Native they have clear instructions on how to modify their code.
- **Tracking** the number of breaking changes over time, understanding the motivation behind each of them and eventually having an idea how to reduce the amount of breaking changes.

Changes that are likely to be present in the next release are listed under `master`.

When adding a new breaking change, follow this template:
```
### New breaking change here

- **Who does this affect**:
- **How to migrate**:
- **Why make this breaking change**: 
- **Severity (number of people affected x effort) (number people affected x amount of work for them)**:
```


# master


### D4157971 (not landed yet, need changes to product code at fb) - @emilsjolander

- Who does this affect: Product developers
- **How to migrate**: ? Fill this in once/if the diff lands.
- Why make this breaking change: Fixes wrong behavior - makes this behave the same as on the web. Repro in https://github.com/facebook/react-native/issues/10603
- Severity (number of people affected x effort) (number people affected x amount of work for them): ?


### Kill deprecated `require('image!...')`: ([ca58e0](https://github.com/facebook/react-native/commit/ca58e0af82797042fabad3873478bc4a9feb7281)) - @davidaurelio 

- Who does this affect: Product developers
- **How to migrate**: Use `<Image source={require('./icon.png')} />`. See http://facebook.github.io/react-native/docs/images.html for more info. In rare cases when you need to directly access native images present in your hybrid app, use `nativeImageSource`.
- Why make this breaking change: The API has been deprecated for a very long time and the alternative is much better.
- Severity (number of people affected x effort) (number people affected x amount of work for them): Medium (hopefully everyone migrated a long time ago).


### Change the `JSCExecutor::callFunctionSync` C++ template ([bd524b](https://github.com/facebook/react-native/commit/bd524bd6e857ada8ec827d65a163d8838e96640b)) - Lukas Piatkowski

- **Who does this affect**: Library authors who call `callFunctionSync` from Obj-C, or from Java via JNI.
- **How to migrate**: Check all the places where you call the native `callFunctionSync`.
- **Why make this breaking change**: Fixes a bug.
- **Severity (number of people affected x effort)**: Very low.


# 0.39

### Move to new C-based implementation of css-layout on Android ([d63ba4](https://github.com/facebook/react-native/commit/d63ba47b59e3261403800c1f741d979a089efb48)) - @astreet

- **Who does this affect**: Product developers.
- **How to migrate**: Previously, developers had to put `flex: 1` in many places it didn't belong in order to work around a bug in css-layout. Now `flex: 1` is treated properly and, unfortunately, this means that your layout may no longer look correct. Specifically, you may see that your layout looks collapsed, or children don't render. The fix is to simply remove `flex: 1` from those containers.
- **Why make this breaking change**: This has shown to be a huge performance win for layout time within FB. Fixes bugs in layout, the layout is closer to web.
- **Severity (number of people affected x effort)**: Low.


### Fix inconsistency with fractional TextInput padding ([aa8540](https://github.com/facebook/react-native/commit/aa85408f568ae9776fef99dcae317def0a07139a)) - @rigdern

- **Who does this affect**: Product developers.
- **How to migrate**: This bugfix can cause padding on TextInputs to be off by one pixel compared to the last version but it most cases you don't need to change your code.
- **Why make this breaking change**: Fixes a bug.
- **Severity (number of people affected x effort)**: Low.

### Android: Disable debug menu when Monkey is running (https://github.com/facebook/react-native/commit/9a8b5d9f4f860f16d0845d537f80bfd2f515ee93) - @ridgern

- Who does this affect: Integration/End-To-End Testers on Android
- **How to migrate**: Use another mechanism if your e2e test requires the dev menu.
- Severity (number of people affected x effort): Low


# 0.38

###  NativeModules IOS: Remove `customDirectEventType` ([aa4428c](https://github.com/facebook/react-native/commit/aa4428cd132bb0d0dbc950b66d3b5f2a3c5b9322)) - @javache
- Who does this affect: People writing 3rd-party modules on iOS
- **How to migrate**: Declare properties of type `RCTDirectEventBlock` instead
- Why make this breaking change: The new API is better and we don't want to keep the old one around.
- Severity (number of people affected x effort): Low


# 0.37

### Remove deprecated APIs and modules ([fa5ad8](https://github.com/facebook/react-native/commit/fa5ad85252be9e5e5a8f04d705463e7ba4cb85e3)) - @satya164
- Who does this affect: Product developers
- **How to migrate**: Import the following modules instead. The API of the new ones should be the same of very similar: AppStateIOS -> AppState, ActivityIndicatorIOS -> Activity, IntentAndroid, LinkingIOS -> Linking, SliderIOS -> Slider, SwitchAndroid, SwitchIOS -> Switch
- Why make this breaking change: These old APIs were designed a long time ago when we didn't think about Android and platform parity at all. We do now :)
- Severity (number of people affected x effort): Medium


### Remove callback support from Clipboard and NetInfo ([fa5ad8](https://github.com/facebook/react-native/commit/fa5ad85252be9e5e5a8f04d705463e7ba4cb85e3)) - @satya164
- Who does this affect: Product developers
- **How to migrate**: Don't pass a callback to `Clipboard.getString()` and `NetInfo.isConnectionExpensive()`. Both methods return a `Promise` now, use the `Promise`.
- Why make this breaking change: A long time ago we didn't a way to return Promises from native to JS so we used to use callbacks. Now Promises should be used everywhere.
- Severity (number of people affected x effort): Low


# 0.36

### Default scrollview to flexShrink to allow views below it ([c43a3f](https://github.com/facebook/react-native/commit/c43a3f5d8412eb0dfe894a192f15efa9c41ab318)) - @emilsjolander.
- Why make this breaking change: Some layouts were broken due to having views below the ScrollView. Not sure if breaking change, we only know of product code this fixed, not broke.


### Fix unconstraint sizing in main axis ([0a9b6b](https://github.com/facebook/react-native/commit/0a9b6bedb312eba22c5bc11498b1cc41363e5f27)) - @emilsjolander
- Who does this affect: Product developers
- **How to migrate**: Most of your layouts will continue to function as before however some of them might not. Typically this is due to having a `flex: 1` which after this change may collapse your component to take zero size due to the implicit `flexBasis: 0` now being correctly treated. Removing the bad `flex: 1` style or changing it to `flexGrow: 1` should solve most if not all layout issues your see after this change.
- Why make this breaking change: The previous behavior was wrong.
- Severity (number of people affected x effort): Medium


### Fix modal resizing on keyboard show ([404b7c](https://github.com/facebook/react-native/commit/404b7cc069471cc8e0277d398751305665f0d3e1)) - @andreicoman11
- Who does this affect: Product developers, Android
- **How to migrate**: No need to change your code. Modals will now resize on keyboard show by default, since that is the default correct Android behavior.
- Why make this breaking change: Resizing is the correct behavior on Android.
- Severity (number of people affected x effort): Low