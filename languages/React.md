# React Cheatsheet

## Create an app

```
$ npx create-react-app my-app-name
```
___

## Files structure

```
my-project
│
└───src
│   │   helpers.js
│   │   index.js
│   │
│   └───components
|   |   |   App.js
│   │   │   MyComponent.js
│   │   │   ...
│   │
│   └───
```
___

## Routes

### Setup Routes

```jsx
// my-projetc/src/index.js

import React from 'react';
import { render } from 'react-dom';
import { BrowserRouter, Match, Miss } from 'react-router';

import App from './components/App';
import Store from './components/Store';
import NotFound from './components/NotFound';

const Root = () => {
  return (
    <BrowserRouter>
      <div>
        <Match exactly pattern="/" component={App} />
        <Match pattern="/store/:storeId" component={Store} />
        <Miss component={NotFound} />
      </div>
    </BrowserRouter>
  )
}

render(<Root/>, document.querySelector('#main'));
```

### Go to route
```jsx
// my-project/src/components/MyComponent.js

import React from 'react';

class MyComponent extends React.Component {
  goToRoute(event) {
    event.preventDefault();
    this.context.router.transitionTo(`/route`);
  }

  render() {
    return (
      <div>
      </div>
    )
  }
}

MyComponent.contextTypes = {
  router: React.PropTypes.object
}

export default MyComponent;
```

___

## Create component

```jsx
// my-project/src/components/MyComponent.js

import React from 'react';

class MyComponent extends React.Component {
  render() {
    return (
      <div>
      </div>
    )
  }
}

export default MyComponent;
```
___

## Methods

### Create a component method

```jsx
// my-project/src/components/MyComponent.js

class MyComponent extends React.Component {
  myMethod(event) {
    console.log('Do something');
  }

  render() {
    return (
      <div>
      </div>
    )
  }
}
```

### Call a method

```jsx
// my-project/src/components/MyComponent.js

class MyComponent extends React.Component {
  myMethod(event) {
    console.log('Do something');
  }

  render() {
    return (
      <div>
        <button type="button" onClick={(e) => this.myMethod(e)}>Click Me</button>
      </div>
    )
  }
}
```
___

## DOM Reference

```jsx
// my-project/src/components/MyComponent.js

class MyComponent extends React.Component {
  logRef(event) {
    console.log(this.refName);
  }

  render() {
    return (
      <div>
        <h1 ref={(el) => {this.refName = el}}>Hello World</h1>
      </div>
    )
  }
}
```
___

## Helpers

### Create helper

```jsx
// my-component/src/helpers.js
export function getSomething() {
  return 'something';
}
```

### Call helpers

```jsx
// my-project/src/components/MyComponent.js

import React from 'react';
import { getSomething } from '../helpers';

class MyComponent extends React.Component {
  render() {
    return (
      <div>
        <input type="text" defaultValue={getSomething()} />
      </div>
    )
  }
}

export default MyComponent;
```
___

## States

```jsx
// my-project/src/components/App.js

import React from 'react';

class App extends React.Component {
  state = {
    myState: {},
  };

  addSomethingToMyState = something => {
    // 1. Take a copy of the existing state
    const myState = { ...this.state.myState };
    // 2. Add our new fish to that fishes variable
    myState[`something${Date.now()}`] = something;
    // 3. Set the new fishes object to state
    this.setState({ myState });
  };

  render() {
    return (
      <ul>
        {Object.keys(this.state.myState).map(key => (
          <li key={key}></li>
        ))}
      </ul>
    )
  }
}

export default App;
```
