This is a **complete** list of breaking changes in each release of React Native.

This document serves two goals:
- **Easier upgrades for people**. The contents of this document are printed by `react-native upgrade` so that when people upgrade their to a new version of React Native they have clear instructions on how to modify their code.
- **Tracking** the number of breaking changes over time, understanding the motivation behind each of them and eventually having a plan to getting to zero breaking changes.

# 0.39

Add breaking changes here

- Commit:
- Who does this affect:
- How to migrate:
- Why make this breaking change:

# 0.38

- Commit: NativeModules IOS: Remove `customDirectEventType` ([aa4428c](https://github.com/facebook/react-native/commit/aa4428cd132bb0d0dbc950b66d3b5f2a3c5b9322))
- Who does this affect: People writing 3rd party modules with Obj-C code
- **Exact steps to migrate (shown by `react-native upgrade`)**: Declare properties of type `RCTDirectEventBlock` instead
- Why make this breaking change: The new API is better and we don't want to keep the old one around.

# 0.37

- Commit: Remove deprecated APIs and modules ([fa5ad8](https://github.com/facebook/react-native/commit/fa5ad85252be9e5e5a8f04d705463e7ba4cb85e3))
- Who does this affect: Product developers
- **Exact steps to migrate (shown by `react-native upgrade`)**: Import the following modules instead. The API of the new ones should be the same of very similar: AppStateIOS -> AppState, ActivityIndicatorIOS -> Activity, IntentAndroid, LinkingIOS -> Linking, SliderIOS -> Slider, SwitchAndroid, SwitchIOS -> Switch
- Why make this breaking change: These old APIs were designed a long time ago when we didn't think about Android and platform parity at all. We do now :)

---

- Commit: Remove callback support from Clipboard and NetInfo ([fa5ad8](https://github.com/facebook/react-native/commit/fa5ad85252be9e5e5a8f04d705463e7ba4cb85e3))
- Who does this affect: Product developers
- **Exact steps to migrate (shown by `react-native upgrade`)**: Don't pass a callback to `Clipboard.getString()` and `NetInfo.isConnectionExpensive()`. Both methods return a `Promise` now, use the `Promise`.
- Why make this breaking change: A long time ago we didn't a way to return Promises from native to JS so we used to use callbacks. Now Promises should be used everywhere.

# 0.36

- Commit: Default scrollview to flexShrink to allow views below it ([c43a3f](https://github.com/facebook/react-native/commit/c43a3f5d8412eb0dfe894a192f15efa9c41ab318))
- Who does this affect: Product developers
- How to migrate: ?
- Why make this breaking change: Some layouts were broken due to having views below the scrollview