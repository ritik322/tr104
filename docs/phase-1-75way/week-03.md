# Week 3 — React Fundamentals

**Dates:** 19 January – 23 January 2026
**Location:** 75Way Technologies, Mohali
**Track:** Multi-stack Training — MERN

---

## Tasks Done

- Began the React portion of the MERN training track with an overview of the library, its component-based philosophy, and the practical problems it solves compared to manipulating the DOM directly with vanilla JavaScript.
- Scaffolded the first React project using Vite as the build tool, with the mentor explaining why the team preferred Vite over the older Create React App for new training exercises due to its significantly faster cold start and hot module replacement.
- Studied the structure of a Vite-generated React project, including the role of `index.html` as the entry point, `main.jsx` as the React mount script, and `App.jsx` as the root component.
- Learned the JSX syntax in depth, including the rules around closing tags, expressions inside curly braces, the use of `className` instead of `class`, and the requirement of a single parent element or a fragment.
- Built several small functional components from scratch, including reusable building blocks like a button, a card, and a form input, and arranged them into composite layouts to understand the component composition model.
- Practised passing data from parent to child components using props, including primitive props, object props, and function props used as event callbacks.
- Worked extensively with the `useState` hook to manage local component state, covering counters, controlled form inputs, toggle switches, and a small to-do list that supported add, edit, and delete operations.
- Studied the React rendering model and the role of the virtual DOM, understanding how React reconciles changes and why state updates trigger re-renders of components and their descendants.
- Introduced the `useEffect` hook for handling side effects such as fetching data from a public API on component mount, and explored the dependency array to control when an effect re-runs.
- Built a small project that fetched a list of users from a public placeholder API, displayed them as cards using component composition, and supported client-side filtering and search through state-driven re-rendering.
- Pushed all daily exercises and the small project to a personal GitHub repository, maintaining a clean commit history with descriptive messages for each feature added.

---

## Technologies Used

- React 18 with functional components and hooks
- Vite as the build tool and development server
- JSX syntax
- React hooks — `useState` and `useEffect`
- JavaScript modules (ES2022+)
- Public REST APIs for data fetching practice
- Visual Studio Code with ES7+ React snippets extension
- Git and GitHub
- Chrome DevTools and React Developer Tools extension

---

## Learnings

- Understood that React's component-based model encourages thinking of the UI as a tree of small, reusable, and independently testable units rather than as a single monolithic page.
- Realised that JSX is not HTML but a JavaScript syntax extension that gets compiled to function calls, which explains restrictions like `className` and the need for a single root element.
- Picked up the practical importance of props being immutable from the child's perspective, and that the only way for a child to update parent state is through a callback function passed down as a prop.
- Learned that the `useState` hook does not merge state updates like the older class-based `setState` did, which means object state has to be spread explicitly when updating a single field.
- Got a clear conceptual model of the virtual DOM and understood that React's performance comes from minimising real DOM operations rather than avoiding them entirely.
- Realised that the dependency array of `useEffect` is one of the most common sources of bugs in React, and that omitting a dependency or including the wrong one can lead to stale closures or infinite re-renders.
- Observed that the React Developer Tools browser extension is indispensable for inspecting the component tree, viewing props and state, and tracking down re-render issues that are not visible in the regular DOM inspector.
