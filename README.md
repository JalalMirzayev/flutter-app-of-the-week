This repository is meant to be a reference for Flutter Widgets presented on YouTube in the [Flutter Widget of the Week](https://www.youtube.com/playlist?list=PLjxrf2q8roU23XGwz3Km7sQZFTdB996iG) series.

# 01. SafeArea

This widget helps to prevent your widgets to disappear in non visible sections.

<img src="/images/01_SafeArea.png" alt="With and without SafeArea" height="400"/>

```dart
ListView(
  children: List.generate(
    100,
    (i) => Text('This is some text')
  ),
)
```


```dart
SafeArea(
  top: true, //SafeArea applied to top
  bottom: true,
  left: false,
  right: true,
  child: ListView(
    children: List.generate(
      100,
      (i) => Text('This is some text'),
    ),
  )
)
```

Wrap the body of a Scaffold

```dart
@override
Widget build(BuildContext context) {
  return Scaffold(
    body: SafeArea(
      child: TonsOfOtherWidgets(),
    ),
  );
}
```
