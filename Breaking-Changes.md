This is a **complete** list of breaking changes in each release of React Native, compiled **as commits land**. This way we can get enough information from owners right when the change is still fresh in their memory.

This document serves two goals:
- **Easier upgrades for people**. The contents of this document are printed by `react-native upgrade` so that when people upgrade their app to a new version of React Native they have clear instructions on how to modify their code.
- **Tracking** the number of breaking changes over time, understanding the motivation behind each of them and eventually having an idea how to reduce the amount of breaking changes.

When adding a new breaking change, follow the below template:
```
## New breaking change here

- **Who does this affect**:
- **How to migrate (shown by `react-native upgrade`)**:
- **Why make this breaking change**: 
- **Severity (people affected x amount of work for them)**:
```

# 0.39

## Fix inconsistency with fractional TextInput padding, https://github.com/facebook/react-native/pull/11003

- **Who does this affect**: All product developers.
- **How to migrate (shown by `react-native upgrade`)**: This bugfix can cause padding on TextInputs to be off by one pixel compared to the last version but it most cases you don't need to change your code.
- **Why make this breaking change**: Fixes a bug.
- **Severity (people affected x amount of work for them)**: Low.

### D4157971 (not landed yet, need changes to product code at fb) - @emilsjolander
- Who does this affect: Any product developer
- **How to migrate (shown by `react-native upgrade`)**: ? Fill this in once/if the diff lands.
- Why make this breaking change: Fixes wrong behavior - makes this behave the same as on the web. Repro in https://github.com/facebook/react-native/issues/10603
- Severity (people affected x amount of work for them): ?

### Android: Disable debug menu when Monkey is running (https://github.com/facebook/react-native/pull/10901) - @ridgern

- Who does this affect: Integration/End-To-End Testers on Android
- **How to migrate**: Use another mechanism if your e2e test requires the dev menu.
- Severity: Low

# 0.38

###  NativeModules IOS: Remove `customDirectEventType` ([aa4428c](https://github.com/facebook/react-native/commit/aa4428cd132bb0d0dbc950b66d3b5f2a3c5b9322)) - @javache
- Who does this affect: People writing 3rd-party modules, iOS
- **How to migrate (shown by `react-native upgrade`)**: Declare properties of type `RCTDirectEventBlock` instead
- Why make this breaking change: The new API is better and we don't want to keep the old one around.
- Severity (people affected x amount of work for them): Low

# 0.37

### Remove deprecated APIs and modules ([fa5ad8](https://github.com/facebook/react-native/commit/fa5ad85252be9e5e5a8f04d705463e7ba4cb85e3)) - @satya164
- Who does this affect: Any product developer
- **How to migrate (shown by `react-native upgrade`)**: Import the following modules instead. The API of the new ones should be the same of very similar: AppStateIOS -> AppState, ActivityIndicatorIOS -> Activity, IntentAndroid, LinkingIOS -> Linking, SliderIOS -> Slider, SwitchAndroid, SwitchIOS -> Switch
- Why make this breaking change: These old APIs were designed a long time ago when we didn't think about Android and platform parity at all. We do now :)
- Severity (people affected x amount of work for them): Medium

### Remove callback support from Clipboard and NetInfo ([fa5ad8](https://github.com/facebook/react-native/commit/fa5ad85252be9e5e5a8f04d705463e7ba4cb85e3)) - @satya164
- Who does this affect: Any product developer
- **How to migrate (shown by `react-native upgrade`)**: Don't pass a callback to `Clipboard.getString()` and `NetInfo.isConnectionExpensive()`. Both methods return a `Promise` now, use the `Promise`.
- Why make this breaking change: A long time ago we didn't a way to return Promises from native to JS so we used to use callbacks. Now Promises should be used everywhere.
- Severity (people affected x amount of work for them): Low

# 0.36

### Default scrollview to flexShrink to allow views below it ([c43a3f](https://github.com/facebook/react-native/commit/c43a3f5d8412eb0dfe894a192f15efa9c41ab318)) - @emilsjolander.
- Fixes a bug: Some layouts were broken due to having views below the ScrollView. Not sure if breaking change, we only know of product code this fixed, not broke.

### Fix unconstraint sizing in main axis ([0a9b6b](https://github.com/facebook/react-native/commit/0a9b6bedb312eba22c5bc11498b1cc41363e5f27)) - @emilsjolander
- Who does this affect: Any product developer
- **How to migrate (shown by `react-native upgrade`)**: Most of your layouts will continue to function as before however some of them might not. Typically this is due to having a `flex: 1` which after this change may collapse your component to take zero size due to the implicit `flexBasis: 0` now being correctly treated. Removing the bad `flex: 1` style or changing it to `flexGrow: 1` should solve most if not all layout issues your see after this change.
- Why make this breaking change: The previous behavior was wrong.
- Severity (people affected x amount of work for them): Medium

### Fix modal resizing on keyboard show ([404b7c](https://github.com/facebook/react-native/commit/404b7cc069471cc8e0277d398751305665f0d3e1)) - @andreicoman11
- Who does this affect: Any product developer, Android
- **How to migrate (shown by `react-native upgrade`)**: No need to change your code. Modals will now resize on keyboard show by default, since that is the default correct Android behavior.
- Why make this breaking change: Resizing is the correct behavior on Android.
- Severity (people affected x amount of work for them): Low