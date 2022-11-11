# Introduction to React

## Contents

- [Introduction to React](#introduction-to-react)
  - [Contents](#contents)
  - [What is React?](#what-is-react)
    - [Why React instead of  vanilla HTML, CSS, and JS?](#why-react-instead-of--vanilla-html-css-and-js)
  - [Alternatives to React](#alternatives-to-react)
  - [Popularity Survey](#popularity-survey)
  - [React Basics](#react-basics)
    - [Creating a new React project](#creating-a-new-react-project)
    - [JSX](#jsx)
    - [How React Works](#how-react-works)
    - [Create our first component](#create-our-first-component)
    - [JSX Rules](#jsx-rules)
    - [Styling components](#styling-components)

## What is React?

[React](https://reactjs.org/) is a JavaScript library for building user interfaces

### Why React instead of  vanilla HTML, CSS, and JS?

- HTML, CSS, and JS are also used for building UIs
- We use libraries like React because they make building UIs easier
- If the UI is complex, building it will be much easier with React
- Development can focus on coding business logic instead of UI boilerplate
- Vanilla works, but has its limitations
  - Complex: everything needs to be **imperatively written** (e.g. create, modify, and append elements; Setting classes; Setting listeners)
  - Developers have to write low-level code repeatedly

  ```JavaScript
  // e.g. in JQuery
  const $someElem1 = $('<div>');
  $someElem1.setText('Elem 1');
  $someParent.append($someElem1);

  // What if we need many of the same element? Let's create an instance again
  const $someElem2 = $('<div>');
  $someElem2.setText('Elem 2');
  $someParent.append($someElem2);

  // and again
  const $someElem3 = $('<div>');
  $someElem3.setText('Elem 3');
  $someParent.append($someElem3);

  // Writing this is longer in vanilla
  ```

- In React, UI code is broken down into **Components**
- Components are reusable building blocks
- These building blocks are combined to create the UI
- Devs write component code and tell React how to compose the UI
- React uses a **declarative** approach
  - Define the desired target state, then React figures out how to update the DOM

  ```JavaScript
  // Sample Element
  function SomeElem(props) {
    return (<div>{props.text}</div>);
  }
  export default SomeElem;

  // In another Component, write what we want as an end result
  function SomeComponent() {
    return (
      <div>
          <SomeElem text='Elem 1'/>
          <SomeElem text='Elem 2'/>
          <SomeElem text='Elem 3'/>
      </div>
    );
  }
  export default SomeComponent;

  // React will handle the creation and rendering of the above component
  ```

  > Technically, **Elements** are the smallest building blocks of React.
  **Components** are built from combining **Elements**. For simplicity, **Components** will be used to refer to both in this document.

React allows developers to code on a 'higher level', which makes building complex UI easier

1. Define the custom elements
2. Define the end result
3. React will manage the elements to reach the end result

## Alternatives to React

- React
  - Lean and focused component-based UI library (Not much other features). Other third-party features need to be installed via external modules/libraries.
- Angular
  - Complete component-based UI framework. Includes many features. Uses TypeScript. Overkill for smaller projects.
- Vue
  - Complete component-based UI framework. Includes core features. Less popular than Angular or React.

## Popularity Survey

<img src='./diagrams/marketshare.svg' style='height: 400px'>

Source [Stack Overflow 2021 Developer Survey](https://insights.stackoverflow.com/survey/2021#section-most-popular-technologies-web-frameworks)

## React Basics

### Creating a new React project

- To start writing React code, we need a React project
- Use `create-react-app` [doc](https://create-react-app.dev/)
  - Tool to create React projects
  - Generates preconfigure folders with basic React files
  - Generates config files for building React apps (for dev and prod)
  - Includes a dev web server that allows to preview the app locally
    - Allows real-time dev/preview

```shell
$ npx create-react-app <APP_NAME>
$ cd <APP_NAME>

# Start the local server
$ npm start
```

- `src/index.js`
  - This is the entry point
    - Includes non-JS code
      - css imports
      - JSX
  - React will transform this module behind the scenes

```javascript
import React from 'react';
import ReactDOM from 'react-dom/client';
import App from './js/components/App';
import './css/index.css';

// This tells React which element to use as the root application
const root = ReactDOM.createRoot(document.getElementById('root'));

// This tells React what to render the App component in the root
root.render(<App />);
```

- `./js/components/App.js`

```javascript
function App() {
  // JSX
  return (
    <div>
      <h1>Hello World React</h1>
    </div>
  );
}

export default App;
```

### JSX

- JSX is essentially HTML inside JS code
- Javascript XML
- This only works because React transforms the JS code to a form that can run on a browser (e.g. look inside `static/js` in inspector)
  - It includes the React/React DOM library package code

### How React Works

1. Build custom components
2. Declare the target state

### Create our first component

- A component in React is just a JS function
- Special: It returns JSX code

```javascript
function MyComponent() {
  return (<h2>Hello Component!</h2>);
}

export default MyComponent;
```

- Import the component in other modules, then use the component like an HTML element

```javascript
import MyComponent from "./components/MyComponent";

function App() {
  return (
    <div>
      <h1>Hello World React</h1>
      <h1>Hello World React Again</h1>
      <MyComponent></MyComponent>
    </div>
  );
}

export default App;
```

### JSX Rules

- Components start with upper-case characters, HTML elements start with lower-case characters
- Components should only return one root element

### Styling components

```javascript
import './ExpenseItem.css'; // import css

function ExpenseItem() {
  return (
    <div className="expense-item">
      <div>March 28 2021</div>
      <div className="expense-item__description">
        <h2>Car Insurance</h2>
        <div className="expense-item__price">$294.67</div>
      </div>
    </div>
  );
}

export default ExpenseItem;
```
