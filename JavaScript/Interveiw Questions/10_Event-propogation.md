## Event propogation
Event propagation in JavaScript describes how events travel through the Document Object Model (DOM) tree. When an event occurs on an element, it can propagate up through the DOM tree, triggering event handlers on parent elements. This process is known as "bubbling." Conversely, events can also propagate down the DOM tree, from the root to the target element, a process known as "capturing." However, capturing is less commonly used than bubbling, which is the default behavior for most events 

## Event bubbling
Event bubbling in JavaScript is a method of event propagation in the HTML Document Object Model (DOM) API. When an event occurs on an element inside another element, and both elements have registered a handler for that event, the event is first captured and handled by the innermost element and then propagated to outer elements. This process starts with the element that triggered the event and then bubbles up to the containing elements in the hierarchy. The addEventListener method is used to register event handlers, where the third parameter, useCapture, is a boolean value that indicates the event phase. By default, useCapture is false, meaning it is in the bubbling phase

## What is event.target & this.target & even.currentTarget
In JavaScript event handling, `event.target`, `this.target`, and `event.currentTarget` are properties of the event object that provide information about the element involved in the event. Understanding the difference between these properties is crucial for handling events correctly, especially in scenarios involving event bubbling and delegation.

- **`event.target`**: This property refers to the element that triggered the event. It is the element on which the event occurred, such as the element that was clicked or the element that received the input. This is the element that is directly involved in the event's occurrence [1].

- **`event.currentTarget`**: This property refers to the element that the event listener is attached to. As the event bubbles up through the DOM, `event.currentTarget` changes to reflect the current element in the bubbling path. This means that if you have an event listener on a parent element, `event.currentTarget` will be that parent element when the event bubbles up to it. This property is useful for event delegation, where you can use it to determine which child element triggered the event [1][2].

- **`this.target`**: This seems to be a typo or misunderstanding, as `this.target` is not a standard property of the event object in JavaScript. The correct property to refer to the element that triggered the event is `event.target`. The `this` keyword in the context of an event handler usually refers to the element that the event listener is attached to, which is equivalent to `event.currentTarget` [2].

Here's an example to illustrate the difference:

```html
<div id="parent">
 <button id="child">Click me</button>
</div>

<script>
document.getElementById('parent').addEventListener('click', function(event) {
 console.log('event.target:', event.target.id); // Outputs "child" if the button is clicked
 console.log('event.currentTarget:', event.currentTarget.id); // Outputs "parent"
});
</script>
```

## Event Delegation
Event delegation is a pattern in JavaScript that leverages the concept of event bubbling to handle events at a higher level in the DOM tree, rather than attaching event listeners to individual elements. This approach is particularly useful when dealing with a large number of elements that need to respond to the same event, such as a list of buttons or links within a container. By attaching a single event listener to a parent element, you can efficiently manage events from its child elements without the need to attach individual event listeners to each child element [1][3][5].

The core idea behind event delegation is to take advantage of the fact that most DOM events bubble up through the DOM tree. When an event occurs on a child element, it propagates up to its parent elements. By setting an event listener on a parent element, you can catch events from its children. Inside the event handler, you can use the `event.target` property to determine which child element triggered the event. This allows you to write a single piece of code that can handle events from multiple elements [1][3][5].

Here's a basic example of event delegation:

```html
<div id="parent">
 <button>Button 1</button>
 <button>Button 2</button>
 <button>Button 3</button>
</div>

<script>
 document.getElementById('parent').addEventListener('click', function(event) {
    if(event.target.tagName === 'BUTTON') {
      console.log("Button was clicked:", event.target.innerText);
    }
 });
</script>
```

In this example, a single event listener is attached to the parent `div`. When any button within the `div` is clicked, the event bubbles up to the `div`, and the event listener checks if the event's target is a button. If so, it logs a message to the console. This approach is efficient and scalable, especially when dealing with dynamic content where elements may be added or removed [1][3][5].

Event delegation offers several benefits:

- **Performance**: It reduces the number of event listeners, which can improve performance, especially in applications with a large number of elements [5].
- **Simplicity**: It simplifies the code by using a single event listener instead of multiple ones [1][3].
- **Flexibility**: It works well with dynamic content, as you don't need to reattach event listeners when elements are added or removed [1][3].

In summary, event delegation is a powerful technique for handling events in JavaScript, offering a more efficient and scalable way to manage events from multiple elements by leveraging event bubbling [1][3][5].
oria.com/javascript-event-delegation-explained
