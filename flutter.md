---
description: >-
  A Flutter plugin for making payments via IppoPay Payment Gateway. Fully
  supports Android and iOS.
---

# Flutter

## IppoPay Payment

[![pub package](https://img.shields.io/pub/v/ippo\_pay.svg)](https://pub.dev/packages/ippo\_pay)

A Flutter plugin for making payments via IppoPay Payment Gateway. Fully supports Android and iOS.

### Installation

In the `dependencies:` section of your `pubspec.yaml`, add the following line:

```yaml
ippo_pay: ^0.0.1
```

Import in your project:

```dart
import 'package:ippo_pay/ippo_pay.dart';
```

### Create Order

Create order from Server side using below API and get the Order id. [Click here](https://docs.ippopay.com/server-side-integrations/rest-api#create-order) to know how to create a order.

### Basic Usage

```dart
import 'dart:convert';

import 'package:flutter/material.dart';
import 'dart:async';

import 'package:flutter/services.dart';
import 'package:ippo_pay/ippo_pay.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatefulWidget {
  @override
  _MyAppState createState() => _MyAppState();
}

class _MyAppState extends State<MyApp> {
  TextEditingController orderIdTextField = new TextEditingController();
  final key = new GlobalKey<ScaffoldState>();

  @override
  void initState() {
    super.initState();
    initPlatformState();
  }

  // Platform messages are asynchronous, so we initialize in an async method.
  Future<void> initPlatformState() async {
    if (orderIdTextField.text.trim().isNotEmpty) {
      try {
        IppoPay.initSdk("Public_Key");
        IppoPay.setLogVisible(true);
        var result = await IppoPay.makePayment(
            json.encode({"order_id": orderIdTextField.text}));
        print(result);
      } on Exception catch (exception) {}
    } else {
      key.currentState.showSnackBar(new SnackBar(
        content: new Text("Please enter orderid"),
      ));
    }
    // Platform messages may fail, so we use a try/catch PlatformException.

    // If the widget was removed from the tree while the asynchronous platform
    // message was in flight, we want to discard the reply rather than calling
    // setState to update our non-existent appearance.
    if (!mounted) return;

    setState(() {
      // _platformVersion = platformVersion;
    });
  }

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        key: key,
        appBar: AppBar(
          title: const Text('Ippopay Example'),
        ),
        body: Container(
          child: Center(
            child: Column(
              crossAxisAlignment: CrossAxisAlignment.center,
              mainAxisAlignment: MainAxisAlignment.center,
              children: [
                Container(
                  margin: EdgeInsets.all(20),
                  child: TextField(
                    controller: orderIdTextField,
                    decoration: InputDecoration(hintText: "Enter the Order id"),
                  ),
                ),
                InkWell(
                  onTap: () {
                    initPlatformState();
                  },
                  child: Container(
                    margin: EdgeInsets.all(20),
                    height: 50,
                    color: Colors.blue,
                    child: Center(
                      child: Text(
                        "Proceed Payment",
                        style: TextStyle(color: Colors.white, fontSize: 18),
                      ),
                    ),
                  ),
                )
              ],
            ),
          ),
        ),
      ),
    );
  }
}
```

Note: If you're using the IppoPay public as a string in flutter, remember to escape the $ dollar signs although it is recommended to load these from your backend

```
IppoPay.initSdk("YOUR_PUBLIC_KEY");
```
