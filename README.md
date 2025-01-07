# Express.js Route Handler Missing Error Handling for Invalid User ID

This repository demonstrates a common error in Express.js route handlers:  missing error handling for invalid input.  Specifically, this example shows a route that retrieves a user by ID.  If the provided ID is not a valid number, the application will likely crash or return an unexpected error.

The `bug.js` file contains the buggy code. The `bugSolution.js` file provides a corrected version with proper error handling.

## Bug

The primary issue is the lack of error handling when parsing the `userId` from the request parameters.  If `req.params.id` is not a number, `parseInt(userId)` will return `NaN`, causing the `users.find()` method to fail silently, or, depending on the implementation, throw an error.

## Solution

The solution incorporates error handling to gracefully manage cases where the `userId` is not a valid number.  It checks for `isNaN` and returns a 400 Bad Request if the ID is invalid.