<a href="https://www.buymeacoffee.com/cetorres" target="_blank"><img src="https://img.shields.io/badge/Donate-Buy%20Me%20A%20Coffee-yellow.svg" alt="Buy Me A Coffee" style="height: auto !important;width: auto !important;" ></a>

# Dropdown form field

A dropdown form field using a dropdown button inside a form field.

## Demo

<img src="https://github.com/priyamshah112/dropdown_formfield/blob/master/screenshot.gif" width="300" />

## Features

- Can be used as regular form field.
- Simple to implement.
- Simple and intuitive to use in the app.
- Provides validation of data.
- Provides requirement of the field.
- Follows the app theme and colors.
- backgroundColor field for User choice color.
- Icon field for UI enhancement.

## Example

```dart
import 'package:flutter/material.dart';
import 'package:dropdown_formfield/dropdown_formfield.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: MyHomePage(),
    );
  }
}

class MyHomePage extends StatefulWidget {
  @override
  _MyHomePageState createState() => _MyHomePageState();
}

class _MyHomePageState extends State<MyHomePage> {
  String _myActivity;
  String _myActivityResult;
  final formKey = new GlobalKey<FormState>();

  @override
  void initState() {
    super.initState();
    _myActivity = '';
    _myActivityResult = '';
  }

  _saveForm() {
    try {
      print(_myActivity);
      var form = formKey.currentState;
      if (form.validate()) {
        form.save();
        setState(() {
          _myActivityResult = _myActivity;
        });
      }
    }
    catch(e){
      print(e);
      _myActivityResult = "";
    }
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Dropdown Formfield Example'),
      ),
      body: Center(
        child: Form(
          key: formKey,
          child: Column(
            mainAxisAlignment: MainAxisAlignment.start,
            children: <Widget>[
              Container(
                padding: EdgeInsets.all(16),
                child: DropDownFormField(
                  backgroundColor:Color(0xffffaf4ff),
                  icon: Icon(
                    Icons.question_answer,
                    color: Color(0xFF03A9F4),
                  ),
                  titleText: 'My workout',
                  hintText: 'Please choose one',
                  value: _myActivity,
                  onSaved: (value) {
                    setState(() {
                      _myActivity = value;
                    });
                  },
                  onChanged: (value) {
                    setState(() {
                      _myActivity = value;
                    });
                  },
                  dataSource: [
                    {
                      "display": "Running",
                      "value": "Running",
                    },
                    {
                      "display": "Climbing",
                      "value": "Climbing",
                    },
                    {
                      "display": "Walking",
                      "value": "Walking",
                    },
                    {
                      "display": "Swimming",
                      "value": "Swimming",
                    },
                    {
                      "display": "Soccer Practice",
                      "value": "Soccer Practice",
                    },
                    {
                      "display": "Baseball Practice",
                      "value": "Baseball Practice",
                    },
                    {
                      "display": "Football Practice",
                      "value": "Football Practice",
                    },
                  ],
                  textField: 'display',
                  valueField: 'value',
                ),
              ),
              Container(
                padding: EdgeInsets.all(8),
                child: RaisedButton(
                  child: Text('Save'),
                  onPressed: _saveForm,
                ),
              ),
              Container(
                padding: EdgeInsets.all(16),
                child: Text(_myActivityResult),
              )
            ],
          ),
        ),
      ),
    );
  }
}

```

## License

This project is licensed under the BSD License. See the LICENSE file for details.
