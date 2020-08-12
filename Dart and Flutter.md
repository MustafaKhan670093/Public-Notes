# Learning How To Program In Dart + Use Flutter

### Introduction

Dart is a client-optimized language developed by Google for fast apps on any platform. Flutter is an open-source UI software development kit created by Google as well. It is used to develop applications for Android, iOS, Linux, Mac, Windows, Google Fuchsia and the web from a single codebase. The two go hand in hand as flutter apps are created by programming in dart. 

### Process

I am learning how to program in dart and to use flutter by following this tutorial: https://www.youtube.com/watch?v=x0uinJvhNxI. I am documenting key points that I have learned and which I find important to know in this document. My goal with learning Dart + Flutter is to be able to improve my skills in rapid prototyping by creating functioning apps.

1. **Conditional** Statements In Dart

   ```
   void main() {
    var userName = 'Mustafa';
    var password = 'test';
    var age = 98;
  
    if (userName == 'Mustafa' && (password == 'test' || age > 18)) {
      print('Logged In!');
    }
    else if (true) {
      print('Overruled!');
    }
    else {
      print('Failed!');
    }
   }
   
   //The code above is a demonstration fo how conditional statements work in dart. 
   //Note that && stands for 'and' while || stands for 'or'.
   ```

2. **Notes** on project.
   
   Completed version of entire project can be found here: https://github.com/MustafaKhan670093/Personality-Test-App.

   ```
   import 'package:flutter/material.dart';

    //void indicates that main will return no output.
    void main() {
      runApp(MyApp());
    }

    // void main() => runApp(MyApp());      This is another way to tell dart that
    //this is a function with only one expression that needs to be executed.

    class MyApp extends StatelessWidget {
      void answerQuestion() {
        print('Answer chosen!');
      }
    @override
    Widget build(BuildContext context) {
      var questions = [
        'What\'s your favourite colour?',
        'What\'s your favourite animal?'
      ];
      return MaterialApp(
        home: Scaffold(
          appBar: AppBar(
            title: Text('First App'),
          ),
          //Note that body only takes in one widget, so we put a column widget,
          //one of the many control/styling widgets that help with the layout of the app.
          //If you wanted items next to each other instead of above each other,
          //you should use the Row() widget.
          //Additionally, note that <Widget>[] would tell Dart that the following list will be full of widgets.
          //However, due to type-inference we don't need to state that as soon as we populate [].
          body: Column(
            children: [
               Text(
                  questions.elementAt(0),      //This can also be written as questions[0]. Note also that wiriting . after a list like 'questions' gives many
                                               //different ways one can go through a list pre-built into dart.
               ),
              RaisedButton(
                child: Text('Answer 1'),
                onPressed:
                    answerQuestion, //We passs the name of the function (by removing parenthesis) instead of the result (by calling the function with parenthesis). 
                                    //This is because onPressed takes in a function. The result would be a value of void, not a function and so we'd get an error.
              ),
              RaisedButton(
                child: Text('Answer 2'),
                onPressed: () => print('Answer 2 Chosen!'),
              ),
              RaisedButton(
                child: Text('Answer 3'),
                onPressed: () {
                  // ... more complex function
                  print(
                      'Answer 3 Chosen!'); //For answer 2 and answer 3, we are calling an anonymous function. This is useful if the function being called only       
                                           //really needs to be called once in the program. There isn't much of a need to store it elsewhere and call it.
                },
                //Side note: This anonymous function is still being named. It is only executed when pressed. If we were to add another () at the end of the function
                //we defined, it would then be called as the program begins and we would get an error (as explained before).
              ),
            ],
          ),
        ),
      );
      //Note that Scaffold gives a base UI that an app can be built upon
      //Click control + space between the parentheses in Scaffold to see what
      //arguments are available.
    }
   }
   ```
   
