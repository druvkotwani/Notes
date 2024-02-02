Babel is a JavaScript compiler that is primarily used to convert ECMAScript 2015+ code into a backwards compatible version of JavaScript that can run in current and older browsers or environments [1][2]. It allows developers to write the latest JavaScript syntax and features, and then compiles it into a version that is compatible with older browsers [3][4].

In the context of React, Babel plays a crucial role. React uses JSX, a JavaScript XML-like syntax extension, which is not understood by older browsers. Babel helps by transforming this JSX syntax into regular JavaScript that can be executed by older browsers [1][4].

Here's an example of how Babel transforms code:

```javascript
// Babel Input: ES2015 arrow function
[1, 2, 3].map((n) => n + 1);

// Babel Output: ES5 equivalent
[1, 2, 3].map(function (n) {
  return n + 1;
});
```

[2]

Babel is highly customizable and extensible with plugins and presets. Plugins are configuration details for Babel to transpile the code that supports a number of plugins, which could be used individually. Presets have a set of plugins that instruct Babel to transpile in a specific mode [3].

To use Babel with React, you would typically install it via npm or Yarn, and then configure it using a `.babelrc` file in your project's root directory. This configuration file specifies the presets and plugins that Babel should use to modify the code [4].

---

Yes, React internally uses Babel or similar tools to convert JSX to JavaScript. JSX is a JavaScript extension syntax used in React to easily write HTML and JavaScript together. However, the browser doesn't understand JSX because it's not valid JavaScript code. Therefore, a tool like Babel is used to convert JSX into browser-understandable JavaScript code [0][2].

When Babel executes JSX, it converts it into `React.createElement` calls. For instance, consider the following JSX code:

```javascript
class JSXDemo extends React.Component {
  render() {
    return <h1>This is JSX</h1>;
  }
}
```

After being processed by Babel, it becomes:

```javascript
class JSXDemo extends React.Component {
  render() {
    return React.createElement("h1", null, "This is JSX");
  }
}
```

In the above code, the JSX `<h1>This is JSX</h1>` is converted into `React.createElement("h1", null, "This is JSX")` [0].

However, starting with React 17, there is a new JSX transform that allows you to use JSX without importing React. This is possible thanks to the introduction of the new JSX transform, which modifies how JSX is transformed into JavaScript [4].
