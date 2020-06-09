Widget works similar like Row and Column but has additional logic to prevent children from lying outside of visible screen space.

<img src="/images/04_Wrap.png" alt="Wrap" height="100"/>

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
