# Table of Contents
- [Event Loop](#event-loop)
- [Hoisting](#hoisting)
- [Strict mode](#strict)
- [async await](#async)
- [Event listeners](#js-events)
- [MediaQueryList.addListener()](#mql)
- [Symbols](#symbols)

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

## Strict mode <a  name="strict"></a>
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
<br />
## Event listeners <a name="js-events"></a>
- The addEventListener method is the most preferred way to add an event listener to window, document or any other element in the DOM.<br />
- Sometime we don’t want an HTML element to behave in the way it is supposed to behave in default. In such a case, we can use Event.preventDefault().<br />
- In order to remove an event listener from an element, we need to call the removeEventListener method with the event name and the function name.<br />
- Bubbling and capturing are the 2 models that events use to propagate<br />.
A click on a child element will always propagate to its parents, unless you stop the propagation.<br />
Those event listeners will be called in order, and this order is determined by the event bubbling/capturing model used.<br />

Bubbling means that the event propagates from the item that was clicked (the child) up to all its parent tree, starting from the nearest one.<br />
Capturing is the opposite: the outer event handlers are fired before the more specific handler. By default all events bubble.<br />
You can choose to adopt event capturing by applying a third argument to addEventListener, setting it to true:<br />
Note that first all capturing event handlers are run.<br />

Then all the bubbling event handlers.<br />

The order follows this principle: the DOM goes through all elements starting from the Window object, and goes to find the item that was clicked. While doing so, it calls any event handler associated to the event (capturing phase).<br />

Once it reaches the target, it then repeats the journey up to the parents tree until the Window object, calling again the event handlers (bubbling phase).<br />
You can stop the propagation by calling the stopPropagation() method of an Event, usually at the end of the event handler:<br />
## MediaQueryList.addListener() <a name="mql" ></a>
```
var mql = window.matchMedia('(max-width: 600px)');

function screenTest(e) {
  if (e.matches) {
    /* the viewport is 600 pixels wide or less */
    para.textContent = 'This is a narrow screen — less than 600px wide.';
    document.body.style.backgroundColor = 'red';
  } else {
    /* the viewport is more than than 600 pixels wide */
    para.textContent = 'This is a wide screen — more than 600px wide.';
    document.body.style.backgroundColor = 'blue';
  }
}

mql.addListener(screenTest);
```
<br />
## Symbols <a name="symbols"></a>
- Every symbol value returned from Symbol() is unique.  A symbol value may be used as an identifier for object properties; this is the data type's only purpose. <br />
- if you want to have unique object keys that cannot be overriden unless using the symbol that created it. see [https://www.youtube.com/watch?v=DHrYasp1OTw]<br />
[![Symbols](http://img.youtube.com/vi/DHrYasp1OTw/0.jpg)](http://www.youtube.com/watch?v=DHrYasp1OTw "Symbols")<br />
