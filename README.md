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

# 02. Expanded

This widget helps to prevent your widgets to disappear in non visible sections.

Without Expanded
```dart
Row(
  children: [
    MyWidget(),
    MyWidget(),
    MyWidget(),
    MyWidget(),
  ],
)
```

<img src="/images/02_Expanded.png" alt="With and without Expanded" height="100"/>

With Expanded (without flex)

```dart
Row(
  children: [
    MyWidget(),
    Expanded(
      child: MyWidget(),
    ),
    MyWidget(),
    Expanded(
      child: MyWidget(),
    ), 
  ],
)
```

With Expanded (with flex)

```dart
Row(
  children: [
    MyWidget(),
    Expanded(
      flex: 2,
      child: MyWidget(),
    ),
    MyWidget(),
    Expanded(
      flex: 1,
      child: MyWidget(),
    ), 
  ],
)
```
