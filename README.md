This repository is meant to be a reference for Flutter Widgets presented on YouTube in the [Flutter Widget of the Week](https://www.youtube.com/playlist?list=PLjxrf2q8roU23XGwz3Km7sQZFTdB996iG) series.

# Table of Contents
1. [SafeArea](#safearea)
2. [Expanded](#expanded)
3. [Wrap](#wrap)

# SafeArea

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

# Expanded

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

# Wrap

Widget works similar like Row and Column but has additional logic to prevent children from lying outside of visible screen space.

<img src="/images/03_Wrap.png" alt="Wrap" height="400"/>

```dart
Wrap(
  alignement: WrapAlignement.end,
  spacing: 10.0,
  runSpacing: 20.0,
  children: [
    MyWidget(),
    MyWidget(),
    MyWidget(),
    MyWidget(),
    MyWidget(),
  ],
)
```
