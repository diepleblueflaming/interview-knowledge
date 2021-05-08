# IMPORTANT JS CONCEPT
<hr>

## JS EVENT LOOP, CALLSTACK, EVENT TABLE, CALLBACK QUEUE, JOB/EVENT QUEUE, HEAP

1. **CALL STACK**
   <br>
   - Where all javascript code gets pushed in and executed one by one and gets popped out once the execution is done.
     <br><br>
2. **EVENT TABLE**
   <br>
    - Event table responsible for moving all asynchronous code to callback/event queue after specified time.
    <br><br>
3. **HEAP**
  <br>
  - HEAP is where memory allocation happens for all variable that is defined in program.
  <br><br>
4. **Callback queue** (Include Task Queue(also known as Macro Task) and Job Queue(Micro Task))
  - Callback queue is where all asynchronous code gets pushed to and wait for the execution.
  - Task Queue
    - Task Queue where asynchronous code like: callback of an event, callback in setTimeout, setInterval, code from a console or `<script>` tag gets pushed to.
    - A new JavaScript program or subprogram is executed (such as from a console, or by running the code in a `<script>` element) directly.
    - An event fires, adding the event's callback function to the task queue.
    - A timeout or interval created with `setTimeout()` or `setInterval()` is reached, causing the corresponding callback to be added to the task queue.
  - Job Queue
    - is where all codes in thenable method(callback method) of a Promise are added to once when Promise is resolved.
    - Have priority than Task Queue. 
  - Event Loop
    - Event loop keeps running continuously and check Call Stack. There are two case:
    - If Call Stack is not empty(has any statement to execute) then it will not check the callback queue.
    - If Call Stack is empty, it will check the Callback Queue(both [Task Queue] and [Job Queue]). First it will check Job Queue and then check Task Queue. If [Callback Queue] not empty it will take first event from [Callback Queue] and push it to [Call Stack] to execution.
<br><br>
5. **SET TIMEOUT, SET INTERVAL**
  - setTimeout
    - Allows us run a function once after specific delay milliseconds.
    - setTimeout return a "timer identifier".
    - To cancel the execution of setTimout/setInterval we should call `clearTimeout` with the "timer identifier" returned from setTimeout.
    - Zero delay scheduling with `setTimeout(func, 0)` (the same as `setTimeout(func)`) is used to schedule the call “as soon as possible, but after the current script is complete”.
    - If we omit the second parameter or pass a negative number, the value "0" will be used.
  <br><br>
  - setInterval 
    - Allow us to run a function regular after specific delay times.
    - setInterval return a "timer identifier". 
    - To cancel the execution of `setInterval` we should call `clearInterval` with the "timer identifier" returned from clearInterval. 
    - Zero delay scheduling with `setInterval(func, 0)` is used to schedule the call “as soon as possible, but after the current script is complete”. 
    - If we omit the second parameter or pass a negative number, the value "0" will be used.
  <br><br>
6. **PROMISE**
  - A promise is an object that may produce a single value some time in the future
  - A promise is maybe in one of three possible state:
    - Pending: when create new promise and not yet fulfilled or rejected.
    - Fulfilled: when `resolve()` was called.
    - Rejected: when `reject()` was called.
  - A promise is settled if it is not pending.
  - A promise is settled it can not be resettled. Calling `resolve()` or `reject()` again will have no effect.
  - Every promise must supply a `.then()` method and `.then()` method may be called many times on the same promise.
  - Then method have two optional function are: onFulfilled and onRejected.
    - onFulfilled: will be called when promise fulfilled.
    - onRejected: will be called when promise is rejected.
  - We can use the `.catch()` method to handle the error occurring in [handleSuccess] of the then method.
  - There are 6 useful method in Promise class:
    - `Promise.reject()` returns a rejected promise.
    - `Promise.resolve()` returns a resolved promise.
    - `Promise.race()` takes an array (or any iterable) and returns a promise that resolves with the value of the first resolved promise in the iterable, or rejects with the reason of the first promise that rejects.
    - `Promise.all()` takes an array (or any iterable) and returns a promise that resolves when all the promises in the iterable argument have resolved, or rejects with the reason of the first passed promise that rejects. 
    - `Promise.allSettled()` method returns a promise that resolves after all the given promises have either fulfilled or rejected, with an array of objects that each describes the outcome of each promise.
    - `Promise.any()` takes an iterable of Promise objects and, as soon as one of the promises in the iterable fulfills, returns a single promise that resolves with the value from that promise. If no promises in the iterable fulfill (if all the given promises are rejected), then the returned promise is rejected with an AggregateError.
  <br><br>
7. **Async and Await**
  - The `async` keyword before a function has two effects:
    - Makes it always return a promise. 
    - Allows `await` keyword to be used in it. 
  - The `await` keyword before a promise makes JavaScript wait until that promise settles, and then:
    - If it’s an error, the exception is generated — same as if throw error were called at that very place. 
    - Otherwise, it returns the result.
<br><br>
8. **Closure**
  - A closure is the combination of a function bundled together (enclosed) with references to its surrounding state (the lexical environment). 
  - In other words, a closure gives you access to an outer function’s scope from an inner function even outer function has finished.
  - In JavaScript, closures are created every time a function is created, at function creation time.
  - All function in JS is closure.
<br><br>
9. **Scope**
  - Global Scope: There is only one Global Scope in a Javascript Document i.e. area outside all the functions and how you can identify a global scope is that the variable defined in the global scope can be accessed anywhere in the code.
  - Local Scope:
    - Variables declared inside functions are local to the function and is bound to the corresponding local scope.
    - Those variables cannot be accessed outside the functions.
    - The local scope can be further divided into function scope and block scope:
      - Function scope is within the function.
      - Block scope is within curly brackets.
  - Lexical Scoping defines how variable names are resolved in nested functions: inner functions contain the scope of outer functions.
<br><br>
10. **var, let, const**
  - `var` declarations are globally scoped or function scoped while let and const are block scoped.
  - `var` can be updated and re-declared within its scope. 
  - `let` variables can be updated but not re-declared.
  - `const` variables can neither be updated nor re-declared.
  - They are all hoisted to the top of their scope. While `var` variables are initialized with undefined `let` and `const` variables are not initialized.
  > Meaning: The block of code is aware of the variable, but it cannot be used until it has been declared.
    Using a let or const variable before it is declared will result in a ReferenceError.
    The variable is in a "temporal dead zone" from the start of the block until it is declared.
    While var and let can be declared without being initialized, const must be initialized during declaration.
  - The `let` and `const` does not create properties of the window object when declared globally (in the top-most scope).    
    

