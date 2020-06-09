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

<img src="/images/03_Expanded.png" alt="With and without Expanded" height="100"/>

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
