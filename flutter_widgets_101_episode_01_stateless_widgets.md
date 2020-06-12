# Stateless Widgets

This file explains how to extract a stateless widget as a reusable component. Let us have a look at the code. There are three positions in the code.
CODE01 is followed by a `DecoratedBox`. CODE02 does the same thing as the `DecoratedBox` by using the stateful widget CODE03.

```dart
import 'package:flutter/material.dart';

void main() {
  runApp(new DogApp());
}

class DogApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
        title: 'My Dog App',
        home: Scaffold(
          appBar: AppBar(
            title: Text('Yellow Lab'),
          ),
          body: Center(
            child: Column(
              children: [
                DecoratedBox(
                    decoration: BoxDecoration(color: Colors.lightBlueAccent),
                    child: Padding(
                      padding: const EdgeInsets.all(8.0),
                      child: Text('Nico'),
                    )),
                SizedBox(
                  height: 8.0,
                ),
                DogName(name: 'Nico'),
              ],
            ),
          ),
        ));
  }
}

class DogName extends StatelessWidget {
  final String name;
  
  // The @required annotation is use to show that the optional parameter is required.
  // Normall we only have to use this for multiple named parameters.
  const DogName({@required this.name}): assert(name != null);

  @override
  Widget build(BuildContext context) {
    return DecoratedBox(
        decoration: BoxDecoration(color: Colors.lightBlueAccent),
        child: Padding(
          padding: const EdgeInsets.all(8.0),
          child: Text(name),
        ));
  }
}
```
