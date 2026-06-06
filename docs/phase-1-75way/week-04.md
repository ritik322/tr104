# Week 4 — Express, MongoDB, and Full MERN Integration

**Dates:** 26 January – 30 January 2026
**Location:** 75Way Technologies, Mohali
**Track:** Multi-stack Training — MERN

---

## Tasks Done

- Began the final week of the MERN portion of the training by introducing Express as the de facto minimal web framework for Node.js, building on the raw `http` module work covered in Week 2.
- Studied the structure of an Express application, including the role of the application object, route handlers, the request and response objects, and the middleware pipeline.
- Built several small REST APIs from scratch, including endpoints for the standard CRUD operations on an in-memory list of resources, and tested each endpoint thoroughly using Postman.
- Practised writing custom middleware functions for cross-cutting concerns such as request logging, JSON body parsing, and basic error handling, and observed how the order of middleware registration affects the request flow.
- Used built-in and third-party middleware including `express.json()` for parsing JSON request bodies, `cors` for enabling cross-origin requests, and `morgan` for HTTP request logging during development.
- Transitioned to the database half of the curriculum with an introduction to MongoDB as a document-oriented NoSQL database, covering BSON, collections, documents, and the practical implications of a schemaless data model.
- Set up a free MongoDB Atlas cluster, connected to it from a Node.js application using the Mongoose ODM, and configured connection strings through environment variables loaded with `dotenv`.
- Studied Mongoose schemas and models, defining schemas with field types, default values, and validation rules, and used the generated model methods like `find`, `findById`, `create`, `updateOne`, and `deleteOne` for database operations.
- Built a complete CRUD REST API for a small notes application, with Express routes mapping to Mongoose model methods, proper status codes for success and failure cases, and validation errors surfaced to the client in a consistent JSON shape.
- Connected the React application from Week 3 to the new Express + MongoDB backend, replacing the public placeholder API with a self-hosted API, and observed the complete MERN data flow from the React form to the MongoDB collection and back.
- Configured environment variables for both the frontend and the backend, separating development and production configuration cleanly and avoiding hard-coded URLs anywhere in the source code.
- Pushed the complete full-stack project to a personal GitHub repository as a milestone deliverable of the MERN training track.

---

## Technologies Used

- Express (Node.js minimal web framework)
- MongoDB (cloud-hosted via MongoDB Atlas free tier)
- Mongoose ODM
- Postman for API testing
- React 18 with Vite (frontend, integrated with the new backend)
- Middleware packages — `cors`, `morgan`, `express.json()`, `dotenv`
- Visual Studio Code, Git, GitHub
- Chrome DevTools (Network tab for inspecting API calls)

---

## Learnings

- Understood that Express does not impose any particular project structure and that the responsibility for organising routes, controllers, and models cleanly lies entirely with the developer.
- Realised that middleware is one of the most powerful concepts in Express, because it allows cross-cutting concerns to be implemented in a composable way without scattering the same code across every route handler.
- Picked up the importance of always returning consistent JSON shapes for both success and error responses, since a frontend client relies on predictable structures to handle them.
- Learned that MongoDB's schemaless nature does not mean schemaless application code, and that defining strict Mongoose schemas with validation is essential for maintaining data integrity in a real project.
- Understood the conceptual difference between a SQL `JOIN` and Mongoose's `populate` method, and observed that document databases often denormalise data that a relational database would normalise.
- Got first-hand experience of why CORS configuration is necessary as soon as the frontend and backend are served from different origins, even when both are on `localhost` but on different ports.
- Realised that wiring the entire MERN stack together end-to-end consolidated all the previous weeks of training, because every layer (React, Express, MongoDB) had to cooperate for even a single API call to succeed.
