# Unexpected Output in setTimeout Loop Due to Closure

This repository demonstrates a common JavaScript closure issue that arises when using `setTimeout` within a loop.  The expected behavior is to log the numbers 0 through 9 with a one-second delay between each. However, due to the way closures work in JavaScript, the output will be 10 ten times.

## Bug Description
The issue stems from the fact that the `setTimeout` callback function doesn't capture the value of `i` at the time it's created, but instead captures a reference to the variable `i`. By the time the `setTimeout` callbacks finally execute, the loop has already completed, and `i` holds its final value of 10. 

## Solution
The solution involves using an Immediately Invoked Function Expression (IIFE) to create a new scope for each iteration of the loop. This ensures that each callback captures its own copy of the `i` value.