This repository is a reference for Flutter Widgets presented on YouTube in the [Flutter Widget of the Week](https://www.youtube.com/playlist?list=PLjxrf2q8roU23XGwz3Km7sQZFTdB996iG) series.

# Table of Contents
1. [SafeArea](#safearea)
2. [Expanded](#expanded)
3. [Wrap](#wrap)
4. [AnimatedContainer](#AnimatedContainer)
5. [Opacity](#Opacity)
6. [FutureBuilder](#FutureBuilder)
7. [FadeTransition](#FadeTransition)
8. [FloatingActionButton](#FloatingActionButton)
9. [PageView](#PageView)

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

# AnimatedContainer

Helps to animate your widgets by animating the widget state transitions.
You can animate colors, borders, border radii, background images, shadows,
gradients, shapes, padding, width, height, alignement, fransforms, and many more.
```dart
@override
Widget build(BuildContext context) {
  return AnimatedContainer(
    color: _color, // (0xFF00BB00)
    duration: _myDuration, // for controlling duration of animation
    curve: Curves.bounceIn, // add specific curves
    child: SomeOtherWidget(),
  );
}
```

```dart
setState(() {
  _color = Color(0xFF0000FF);
}
)
```

# Opacity

Analog behaviour to hidden from iOS and invisible from Android. Used when you want to remove the widget from the UI but
still want to occupy the same space as with the visible widget. 

```dart
final widgets = [
  MyWidget(Color.green),
  Opacity(
    opacity: 0.0,
    child: MyWidget(Color.blue),
  ),
  MyWidget(Color.yellow),
];
```

Can also be used for blending widgets inside of stack.

```dart
Stack(
  children: [
    MyImageWidget(),
    Opacity(
      opacity: 0.25,
      child: MyGradientWidget(),
    ) 
  ],
)
```

Can also be combined with Animations using AnimatedOpacity.

```dart
Stack(
  children: [
    MyImageWidget(),
    AnimatedOpacity(
      duration: _myDuration, // animation duration
      opacity: _myOpacity, // state to change
      child: MyGradientWidget(),
    ),  
  ],
)
```

# FutureBuilder
Helps to implement features which need time for execution until changes in the app can be updated.

```dart
FutureBuilder(
  future: http.get('http://awesome.data'),
  builder: (context, snapshot) {
      // Check connection state and render placeholder during processing time.
      // Possible other states are ConnectionState.none, ConnectionState.waiting,
      // ConnectionState.active and ConnectionState.done.
      if (snapshot.connectionState == ConnectionState.done) {
        if (snaphot.hasError) {
          return SomethingWentWrong();
        } 
        return AwesomeData(snapshot.data);
      } else {
        return CircularProgressIndicator();
      } 
  }
)
```

# FadeTransition

The Flutter SDK provides simple transitions. One example is the FadeTransition widget.

```dart
// Create the AnimationController.
final controller = AnimationController(
  vsync: this,
  duration: Duration(seconds: 2),
);
// Create the animation.
final animation = Tween(
  begin: 0.0,
  end: 1.0,
).animate(controller);

// Start the animation.
controller.forward();

// It is a good idea to put this into a stateful widget.
FadeTransition(
  opacity: animation,
  child: Text(widget.text));
```

# FloatingActionButton

Positioning the FloatingActionButton (FAB) in a bottomNavigationBar can sometime be challenging. 

```dart
Scaffold(
  floatingActionButton: FloatingActionButton(
    child: Icon(Icons.add),
    onPressed: () {print('I was pressed!')},
  ),
  bottomNavigationBar: BottomAppBar(
    color: Colors.yellow,
    child: Container(height: 50.0),
  ),
  // Set the position.
  // Possible positions are: centerDocked, endDocked
  floatingActionButtonLocation:
    FloatingActionButtonLocation.endDocked,
);
```

# PageView

With this widget you can provide the user the possibility to swipe between different pages.

```dart
final Controller = PageControler(
  initialPage: 1,
);

// Create the PageView.
final pageView = PageView(
  controller: controller,
  scrollDirection: Axis.vertical,
  children: [
    MyPage1Widget(),
    MyPage2Widget(),
    MyPage3Widget(),
  ],
);
```

# Table

Similar to Grid but not scrollable and embedded widgets with different sizes.

```dart
Table(
  // Determine Vertical Alignment.
  // Possible alignments: top, middle, bottom.
  defaultVerticalAlignment: TableCellVerticalAlignment.top,
  border: TableBorder.all(),
  defaultColumnWidth: FractionColumnWidth(.25),
  children: [
    TableRow(
      children: [
        Widewidget(),
        MediumWidget(),
        MediumWidget(),
      ],
    ),
    TableRow(
      children: [
        MediumWidget(),
        NarrowWidget(),
        MediumWidget(),
      ],
    ),
  ],
);
```


