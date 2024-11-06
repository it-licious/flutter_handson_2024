# handson

A hands-on introduction to Flutter development

## Getting Started

After cloning this project, run the app and make sure the app title bar 'IT Licious' is shown.

> Tip: Use F5 for VS Code or Cmd + R for Android Studio to run the app in debug mode.

## Exercise

Now try the following steps:

### 1. Create a UI

Open `tasks_screen.dart`. Build an interface (replacing the `Container()` widget) that looks like this:

```
  ---------------
  | Item 1      |  <- ListView
  | Item 2      |
  | Item 3      |
  |             |
  |             |
  ---------------
  | _           |  <- TextFormField
  ---------------
```

You will need a [`ListView`](https://api.flutter.dev/flutter/widgets/ListView-class.html) with `children`, which are widgets themselves. The items can be `ListTile`s with fixed `title: Text("Item X")` for now.

> Tip: Hot Reload after any code change by saving the file or using Cmd + F5 (VS Code) or Cmd + \ (Android Studio).

For the complete layout, you will need to wrap the `ListView` in a `Column`, making sure the list itself is in an `Expanded` widget to occupy the available vertical space.

> Tip: Cmd + . (VS Code) or Alt + Enter (Android Studio) for quick fixes such as wrapping a widget.

### 2. Convert to a stateful widget

Convert the `StatelessWidget` to a `StatefulWidget`, using the IDE shortcut. This will create a `State<TasksScreen>`.

> Tip: use Cmd + . (VS Code) or Alt + Enter (Android Studio)

Add a screen state by adding a field (a variable in the state class) of type `List<String>`.

> Tip: Instantiate a list using the list operator, such as `["Item 1", "Item 2"]`.

Remove the fixed `children` from your list view and create them instead from your `List<String>`.

> Tip: Map the items in your list using the `map` operator; `items.map((item) => Text(item)).toList()`.

### 3. Modify the state using `setState`

To effectively add items to your state, use `TextFormField`'s `onFieldSubmitted` and call `setState` to add the newly entered value to the existing `List<String>`.

### 4. Allow removing of items

To each `ListTile`, add a `trailing` `IconButton` widget and in the `onPressed` callback remote the specific items from the `List<String`.

```
           IconButton
               |
               v
  ---------------
  | Item 1     X|
  | Item 2     X|
  | Item 3     X|
  |             |
  |             |
  ---------------
  | _           |
  ---------------
```

### 5. Add button

Instead of using the keyboard with `onFieldSubmitted`, add a `TextEditingController` field and use an `ElevatedButton` to add items to the list, using your text controller's `.text` property.

```
  ---------------
  | Item 1     X|
  | Item 2     X|
  | Item 3     X|
  |            X|
  |            X|
  ---------------
  | _     | Add |  <- Row with TextFormField (in Expanded) and ElevatedButton
  ---------------
```

Using the `TextEditingController` you can also clear the input field after adding.

### 6. Animations

Open `pubspec.yaml` and add [`flutter_animate`](https://pub.dev/packages/flutter_animate) as a dependency. Make sure to run 'pub get'.

To your existing `ListView` children, add a simple animation. For example:

```dart
 children: items.map(...).toList().animate(interval: 400.ms).fade(duration: 300.ms),
```

### Bonus: Fix the 'random' removal bug

Enter some items in your list with the same value, such as '1', '2', '3' and '2' and click to remove the last item. It probably removed the first '2' instead of the last. Try to fix this bug.

> Tip: you need to way to uniquely identify your items
