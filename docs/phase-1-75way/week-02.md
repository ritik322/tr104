# Week 2 — Advanced JavaScript and Node.js Foundations

**Dates:** 12 January – 16 January 2026
**Location:** 75Way Technologies, Mohali
**Track:** Multi-stack Training — MERN

---

## Tasks Done

- Continued the MERN training track with a deeper exploration of modern JavaScript features beyond the basics covered in the previous week.
- Studied the JavaScript event loop, the call stack, the task queue, and the microtask queue, and observed through small examples how `setTimeout`, `Promise.then`, and `queueMicrotask` are scheduled differently by the runtime.
- Worked extensively with asynchronous JavaScript, beginning with the callback pattern and the callback hell problem, then moving to promises with `then`, `catch`, and `finally`, and finally to the `async` and `await` syntax for writing asynchronous code in a synchronous style.
- Practised consuming public REST APIs using the browser's `fetch` API and handling JSON responses, error states, and network failures gracefully using `try`/`catch` blocks around `await` calls.
- Explored JavaScript modules using the `import` and `export` syntax, and understood the difference between named exports and default exports as well as the practical implications of each.
- Began the Node.js portion of the curriculum in the second half of the week, starting with the role of Node.js as a server-side JavaScript runtime built on top of the V8 engine.
- Set up small Node.js scripts to read and write files using the `fs` module, work with paths using the `path` module, and accept command-line arguments through `process.argv`.
- Learned the structure of a Node.js project through the `package.json` file, including the meaning of `dependencies` versus `devDependencies`, the `scripts` section, and the role of `package-lock.json` in reproducible installs.
- Installed and used a few popular npm packages such as `nodemon` for auto-restarting the server during development and `dotenv` for managing environment variables outside the source code.
- Built a simple HTTP server from scratch using the built-in `http` module to understand the underlying request and response objects before being introduced to higher-level frameworks like Express in the following week.
- Completed mentor-assigned exercises including a small command-line note-taking application that persisted data to a JSON file and a script that fetched and displayed weather data from a public API.

---

## Technologies Used

- JavaScript (ES2022+) — Promises, `async`/`await`, modules
- Node.js (LTS) with built-in `http`, `fs`, and `path` modules
- npm and `npm init` workflow
- `nodemon` and `dotenv` packages
- Public REST APIs for practice
- Visual Studio Code, Git, GitHub
- Chrome DevTools and Node.js debugger

---

## Learnings

- Understood that JavaScript's single-threaded nature does not mean it is slow at handling concurrent work, because the event loop allows non-blocking I/O through the underlying runtime.
- Realised that promises are not just syntactic sugar over callbacks but a fundamentally different way of representing a future value, with composability through chaining and `Promise.all`.
- Learned that the `async`/`await` syntax does not add new functionality on top of promises but makes asynchronous code dramatically easier to read, write, and debug.
- Got first-hand experience of the difference between resolved and rejected promises and understood why every `await` in production code should be wrapped in a `try`/`catch` block.
- Picked up the conceptual model of Node.js as a JavaScript runtime that exposes operating-system-level capabilities like file I/O and networking, which are not available in the browser.
- Understood that `package.json` is the single source of truth for a Node.js project's identity, dependencies, and scripts, and that it should always be checked into version control.
- Realised that even though high-level frameworks like Express abstract away the raw `http` module, having built a server from scratch makes the abstractions far easier to understand.
