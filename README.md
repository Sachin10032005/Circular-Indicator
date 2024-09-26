# Flutter Determinate Circular Progress Indicator

## Introduction
This Flutter project demonstrates a determinate circular progress indicator. The progress bar fills up gradually, resetting itself once it reaches 100%. It showcases how to use a `CircularProgressIndicator` with a specified value and update the progress using the `setState` method.

## Getting Started
To run this project, you need to have Flutter installed on your machine. If you haven't installed Flutter yet, follow the [official installation guide](https://flutter.dev/docs/get-started/install) to get started.

## Packages Used
This project does not use any third-party packages; it relies solely on Flutter's built-in widgets and libraries.

## Installation
1. Clone the project or create a new Flutter app using the command:

   ```bash
   flutter create progress_example
dependencies:
  flutter:
    sdk: flutter
flutter pub get
### Code Overview

The following Dart code demonstrates how to create a staggered grid layout using the `StaggeredGrid` widget in Flutter.

```dart
import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      theme: ThemeData(
        primarySwatch: Colors.blue,
      ),
      home: ProgressExample(),
    );
  }
}

class ProgressExample extends StatefulWidget {
  @override
  _ProgressExampleState createState() => _ProgressExampleState();
}

class _ProgressExampleState extends State<ProgressExample> {
  double _progressValue = 0.0;

  @override
  void initState() {
    super.initState();
    _updateProgress();
  }

  void _updateProgress() {
    Future.delayed(Duration(milliseconds: 500), () {
      setState(() {
        _progressValue += 0.1;
        if (_progressValue > 1.0) {
          _progressValue = 0.0;
        }
        _updateProgress();
      });
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text("Determinate Circular Progress"),
        backgroundColor: Colors.blue,
      ),
      body: Center(
        child: CircularProgressIndicator(
          value: _progressValue,
          backgroundColor: Colors.grey[200],
          color: Colors.blue,
          strokeWidth: 6.0,
        ),
      ),
    );
  }
}
