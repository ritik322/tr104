# Week 7 — Flutter and Dart for Cross-Platform Mobile

**Dates:** 16 February – 20 February 2026
**Location:** 75Way Technologies, Mohali
**Track:** Multi-stack Training — Mobile

---

## Tasks Done

- Transitioned from the Python web framework portion of the training to the mobile development track, beginning with Flutter as the first cross-platform mobile framework on the curriculum.
- Studied the rationale behind Flutter as a UI toolkit that compiles to native ARM code on both Android and iOS from a single Dart codebase, with the mentor explaining how it differs from the JavaScript bridge approach used by older cross-platform frameworks.
- Installed the complete Flutter development setup on the assigned workstation, including the Flutter SDK, Android Studio with the Android SDK and emulator, and the Flutter and Dart plugins for Visual Studio Code.
- Verified the environment using `flutter doctor` and resolved several setup issues such as missing Android licenses, Java version mismatches, and emulator graphics acceleration settings.
- Spent the first two days learning the Dart programming language, covering variables, type inference with `var` and `dynamic`, null safety with the `?` suffix, functions, classes, named constructors, and asynchronous code with `async`, `await`, and `Future`.
- Scaffolded the first Flutter project using `flutter create` and explored the generated project structure, including the role of `pubspec.yaml` for dependencies and the `lib` directory as the entry point for all Dart source code.
- Studied Flutter's core principle that everything is a widget, including layout elements (`Row`, `Column`, `Container`, `Padding`), visual elements (`Text`, `Image`, `Icon`), and interactive elements (`ElevatedButton`, `TextField`).
- Practised building user interfaces by composing widgets into nested trees, observing how the framework's declarative approach is conceptually similar to React's component model but applied to native mobile UI.
- Explored the difference between `StatelessWidget` and `StatefulWidget`, building small examples of each and understanding when state needs to be encapsulated within a widget versus passed in through the constructor.
- Implemented a small counter application and a simple to-do list application using `setState` to trigger UI rebuilds, and observed how Flutter's rendering pipeline efficiently diffs the widget tree on every state change.
- Used Material Design widgets from the `material` package to build screens that automatically adapt to platform conventions, and explored the Cupertino widget set briefly for iOS-style interfaces.

---

## Technologies Used

- Flutter SDK
- Dart programming language
- Android Studio with Android SDK and AVD emulator
- Visual Studio Code with Flutter and Dart extensions
- Material Design and Cupertino widget libraries
- `pubspec.yaml` for dependency management
- Git and GitHub
- Chrome DevTools (Flutter web debugging) and Flutter DevTools

---

## Learnings

- Understood that Flutter's compilation to native ARM code is a fundamental architectural difference from JavaScript-bridge frameworks, and is the primary reason why Flutter applications generally feel smoother and more responsive on lower-end devices.
- Realised that Dart as a language is conservative and familiar to anyone with a Java or C# background, which makes the transition to Flutter relatively painless once the widget concepts are grasped.
- Picked up the practical implications of Dart's null safety, where the type system itself prevents the most common class of runtime errors that plague languages without similar guarantees.
- Learned that the everything-is-a-widget philosophy is taken very literally in Flutter, including invisible widgets like `Padding`, `Center`, and `SizedBox` that exist purely to influence the layout of their children.
- Got first-hand experience of why Flutter's hot reload is a transformative development experience, because changes to the UI are reflected in the running emulator within seconds without losing the current application state.
- Observed that the conceptual mapping between React and Flutter is strong enough that prior React experience accelerated the learning curve significantly, particularly around the declarative UI mindset and the role of state.
- Understood that while Flutter handles the UI layer beautifully, building a production application still requires choices around state management, navigation, and backend integration that go beyond the core framework.
