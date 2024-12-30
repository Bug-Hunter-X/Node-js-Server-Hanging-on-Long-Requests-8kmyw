# Node.js Server Hanging on Long Requests

This repository demonstrates a common issue in Node.js servers: blocking the event loop with long-running synchronous operations.  The example showcases a simple HTTP server that hangs for 5 seconds on every request, preventing it from handling other requests concurrently.

The solution demonstrates how to address this by using asynchronous operations or offloading long tasks to worker threads.

## Setup

1. Clone the repository.
2. Navigate to the directory.
3. Run `npm install` to install dependencies (none are needed).

## Running the Buggy Code

1. Run `node server.js`.
2. Open multiple browser tabs and visit `http://localhost:3000`. You'll observe that only one request is processed at a time; subsequent requests hang until the first one completes.

## Running the Solution

1. Run `node server-solution.js`.
2. Open multiple browser tabs and visit `http://localhost:3000`.  You'll now see that all requests are handled concurrently without blocking.

## Key Concepts

* **Event Loop:** Node.js is single-threaded and relies on an event loop to handle asynchronous events. Blocking the event loop with synchronous operations prevents other events from being processed.
* **Asynchronous Programming:**  Asynchronous operations (using callbacks, promises, or async/await) don't block the event loop, allowing Node.js to remain responsive.
* **Worker Threads:** For CPU-bound tasks, offloading work to worker threads can prevent blocking of the main event loop.