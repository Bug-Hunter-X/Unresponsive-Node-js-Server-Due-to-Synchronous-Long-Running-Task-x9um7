# Unresponsive Node.js Server

This repository demonstrates a common issue in Node.js where a long-running synchronous operation within the request handler of an HTTP server causes the server to become unresponsive. The event loop is blocked, preventing other requests from being processed.

## Bug

The `bug.js` file contains a server that simulates a long-running task within the request handler. This task keeps the CPU busy for 5 seconds, making the server unresponsive during that time.

## Solution

The `bugSolution.js` file demonstrates how to solve this issue by using asynchronous operations.  Instead of a synchronous `while` loop, the solution uses `setTimeout` to schedule the task to run later. This allows the event loop to continue processing other requests without interruption.

## How to reproduce

1. Clone the repository.
2. Run `node bug.js`.
3. Open multiple browser tabs and try to access `http://localhost:3000/`. You'll notice that subsequent requests will hang until the first one finishes.
4. Run `node bugSolution.js`. You'll notice that this time requests are processed concurrently.