# Stale Closure in React's useEffect Cleanup Function

This repository demonstrates a common but subtle error in React's `useEffect` hook: accessing stale closure state within the cleanup function.  The example showcases how a variable captured in the closure might not hold the most up-to-date value when the cleanup function executes.

## Bug Description
The `count` variable inside the `useEffect` cleanup function is a closure, capturing the value of `count` at the time the effect is created, rather than the current value when the component unmounts. This leads to potentially incorrect logging and can sometimes cause unexpected behavior in more complex scenarios. 

## Solution
The solution involves using a `ref` to access the current value of `count`. Refs bypass the closure problem because they directly reference the latest state value.

## How to reproduce
1. Clone this repo
2. Run `npm install`
3. Run `npm start`
4. Observe the console logs when you increment the counter several times before unmounting the component.