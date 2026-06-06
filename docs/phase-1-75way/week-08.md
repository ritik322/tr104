# Week 8 — React Native and the Evaluation Test

**Dates:** 23 February – 27 February 2026
**Location:** 75Way Technologies, Mohali
**Track:** Multi-stack Training — Mobile + Evaluation

---

## Tasks Done

- Began the final week of the multi-stack training programme with the second mobile framework on the curriculum, React Native, which builds on the React fundamentals covered in Week 3 but targets native mobile platforms instead of the browser.
- Studied how React Native differs from Flutter, with the mentor explaining that React Native bridges JavaScript code to native UI components through a JavaScript runtime, whereas Flutter renders everything itself using its own engine and Skia graphics library.
- Installed the React Native development environment using the Expo toolchain, which significantly simplifies the setup compared to bare React Native projects that require native Android and iOS build tools from the outset.
- Scaffolded the first React Native project using `npx create-expo-app`, explored the generated project structure, and ran the application on both the Android emulator from Week 7 and the Expo Go application on a physical Android device.
- Practised building user interfaces using React Native's core components such as `View`, `Text`, `ScrollView`, `FlatList`, `TextInput`, `TouchableOpacity`, and `Image`, observing the parallels and differences with their browser equivalents.
- Applied styling using React Native's `StyleSheet.create` API and the Flexbox-based layout system, noting that React Native uses Flexbox by default rather than as one option among many.
- Built a small notes application that demonstrated component composition, the `useState` and `useEffect` hooks (carried over directly from web React), local form input handling, and conditional rendering of list items.
- Explored React Navigation as the de facto navigation library for React Native, setting up a stack navigator and a bottom tab navigator to switch between multiple screens within the same application.
- Spent the second half of the week preparing for and appearing in the **evaluation test** that concludes the training programme at 75Way Technologies, which covered all five stacks taught across the previous seven weeks.
- Completed both the written portion of the evaluation (multiple-choice and short-answer questions on core concepts) and the practical portion (building a small full-stack feature within a time limit using a chosen stack).
- Received the project assignment for the next phase of the internship after the evaluation results were reviewed by the mentors, with the assigned project being the **Manage Business** centralized authentication and access management platform on the Next.js + MongoDB stack.

---

## Technologies Used

- React Native with the Expo toolchain
- JavaScript (ES2022+) and JSX
- React hooks — `useState` and `useEffect`
- React Navigation (stack and bottom tab navigators)
- `StyleSheet` API and Flexbox layout
- Expo Go application on a physical Android device for live testing
- Android emulator from Week 7 for parallel testing
- Visual Studio Code with React Native Tools extension
- Git and GitHub

---

## Learnings

- Realised that React Native is significantly easier to pick up for someone already comfortable with React on the web, because the component model, hooks, and JSX syntax are exactly the same and only the rendering targets differ.
- Understood the practical impact of the JavaScript bridge architecture in React Native, including both its benefits (familiar JavaScript ecosystem, code sharing with web) and its limitations (occasional performance overhead for animation-heavy interfaces).
- Picked up the value of the Expo toolchain for prototyping and training scenarios, because it removes the need to maintain native Android and iOS build configurations during the early stages of a project.
- Learned that React Native's reliance on Flexbox as the only layout system is intentional, because it keeps the mental model consistent across platforms and removes the need to learn multiple layout primitives.
- Got a clear comparative view of Flutter and React Native side by side after building similar small applications in both, and understood that the choice between them is often driven by team familiarity rather than technical superiority.
- Observed that the eight weeks of training, although fast-paced, delivered a genuinely broad exposure to the modern web and mobile ecosystem, which made the transition into the project assignment far smoother than starting cold.
- Realised that the evaluation test was less about memorising syntax and more about demonstrating the ability to apply core concepts under time pressure, which mirrors what real project work demands.
