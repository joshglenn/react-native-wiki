# 0.39

Add breaking changes here

- Commit, title:
- Who does this affect:
- How to migrate:
- Why make this breaking change:

# 0.38

- Commit, title: [aa4428c](https://github.com/facebook/react-native/commit/aa4428cd132bb0d0dbc950b66d3b5f2a3c5b9322) NativeModules IOS: Remove `customDirectEventType`
- Who does this affect: People writing 3rd party modules with Obj-C code
- How to migrate: Declare properties of type `RCTDirectEventBlock` instead
- Why make this breaking change: The new API is better and we don't want to keep the old one around.

# 0.37

- Commit, title: [fa5ad8](https://github.com/facebook/react-native/commit/fa5ad85252be9e5e5a8f04d705463e7ba4cb85e3) Remove deprecated APIs and modules
- Who does this affect: Any product developer
- How to migrate: AppStateIOS -> AppState, ActivityIndicatorIOS -> Activity, IntentAndroid, LinkingIOS -> Linking, SliderIOS -> Slider, SwitchAndroid, SwitchIOS -> Switch
- Why make this breaking change: These old APIs were designed a long time ago when we didn't think about Android and platform parity at all. We know better now :)
