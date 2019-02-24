# Table of Contents
- [Event Loop](#event-loop)
- [Hoisting](#hoisting)
- [Strict mode](#strict)
- [async await](#async)

## Event Loop<a name="event-loop"></a>
JavaScript is a single thread programming language. The reason we can deal with concurrency and asynchonous tasks is because the browser is much more than just the runtime. There are WebApis in the browser: DOM, XHR, setTimeout. These are effectively threads that you can make calls to. When you make a call to one of these APIs  They push your callback to the task queue. then the event loop looks at the stack and the task queue, if the stack is empty it then puts the first item of the task queue into the stack.<br />
There reason sometimes we run code inside setTimeout(() => {}, 0); is that we want to defer its execution until the stack is clear.<br />
```setTimeout()``` is not a guaranteed time to execution , its a minimum time to execution. I.E. if you call multiple setTimeouts and they are in the Callback queuethen they are put back in the call stack sequentially and so they wait until the earliest callback is executed.<br />
Callbacks can be two things:<br />
- any function that another function calls.<br />
- a function that is async and its put into the callback queue.<br />
The Browser optimally would like to repaint every 16 milliseconds but it cannot do it if there is code in the stack.<br />
The repaint of render queue is given priority over the callback queue.<br />
- Don't put slow code in the stack because it will block the render Queue and the page will become unresponsive.<br />
## Hoisting <a name="hoisting"></a>
- Hoisting is a JavaScript mechanism where variables and function declarations are moved to the top of their scope before code execution.<br />
- In JavaScript, an undeclared variable is assigned the value undefined at execution and is also of type undefined.<br />
- function declarations are hoisted ```function foo()``` but funtion expressions are not ``` var foo = function()```<br />

## Strict mode <a  name="stric"></a>
Strict mode makes several changes to normal JavaScript semantics:<br />

- Eliminates some JavaScript silent errors by changing them to throw errors.<br />
- Fixes mistakes that make it difficult for JavaScript engines to perform optimizations: strict mode code can sometimes be made to run faster than identical code that's not strict mode.<br />
- Prohibits some syntax likely to be defined in future versions of ECMAScript.<br />
## Async / Await <a name="async"></a>
```
// Function declared as async so await can be used
async function fetchContent() {
  // Instead of using fetch().then, use await
  let content = await fetch('/');
  let text = await content.text();
  
  // Inside the async function text is the request body
  console.log(text);

  // Resolve this async function with the text
  return text;
}

// Use the async function
var promise = fetchContent().then(...);
```
