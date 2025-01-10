# React useEffect Hook: Missing Cleanup Function for setInterval
This repository demonstrates a common error in React's `useEffect` hook: forgetting to include a cleanup function to clear intervals or timeouts.

## The Problem
The `setInterval` function, when used within `useEffect` without a cleanup function, creates a memory leak. Each time the component renders, a new interval is created, leading to multiple intervals running concurrently. This can cause performance issues or unexpected behavior.

## The Solution
The correct approach involves returning a cleanup function from `useEffect`. This function is responsible for clearing the interval before the component unmounts or when the dependencies change. This prevents memory leaks and ensures that the component behaves as expected.

## How to Reproduce
Clone this repository and run `npm install`. Then, run `npm start`. You'll see the counter incrementing every second.  Close the tab or navigate away, and notice the continued counter incrementing in the console (you can use your browser's dev tools to see this).

## How to Fix
Refer to the `bugSolution.js` file for the corrected code. The key change is the addition of a cleanup function (using `clearInterval`) within the `useEffect`'s return statement.