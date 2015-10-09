# react-stateless

Helpers to write stateless functional components in React.

> Write stateless functional components in React with lifecycle methods as pure functions!


### ReactStateless.createClass(specification)

`specification` can be a __[stateless render function](https://facebook.github.io/react/blog/2015/10/07/react-v0.14.html#stateless-functional-components)__
or an __object containing pure stateless lifecycle functions__.

#### Example: component as a function

```javascript
import { React } from 'react';
import { createClass } from 'react-stateless';

function ComponentA(props) {
    return <div>{ props.name }</div>;
}

// React 0.14
export default ComponentA
// Or
export default createClass(ComponentA);
```

#### Example: component as an object

```javascript
import { React } from 'react';
import { createClass } from 'react-stateless';

function shouldComponentUpdate(props, nextProps) {
    return props.name !== nextProps.name;
}

function render(props) {
    return <div>{ props.name }</div>;
}

export default createClass({shouldComponentUpdate, render})
```

#### Supported properties

- `propTypes`
- `defaultProps`
- `displayName` (automatically detected by if your component function or render function is named)

#### Supported methods

- `componentWillMount(props)`
- `componentDidMount(props, refs)`
- `componentWillReceiveProps(props, nextProps, refs)`
- `shouldComponentUpdate(props, nextProps, refs)`
- `componentWillUpdate(props, nextProps, refs)`
- `componentDidUpdate(props, prevProps, refs)`
- `componentWillUnmount(props, refs)`
