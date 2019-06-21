# React Notes

> Reading starts on https://reactjs.org/docs/hello-world.html
>
> Started on 2019-06-18

## Installation

### `npx`
```
npx create-react-app my-app
cd my-app
npm start
```

### Try JSX
To quickly try JSX, (not suitable for production):
1. Add this to the page
```
<script src="https://unpkg.com/babel-standalone@6/babel.min.js"></script>
```
2. Use `type="text/babel"` to all react script tags

### Production JSX
[Link](https://reactjs.org/docs/add-react-to-a-website.html#add-jsx-to-a-project)


## Main Concepts
- JSX
- Use parentheses to avoid the pitfall of automatic semicolon insertion
- "Babel" language definition

- render a React element into a root DOM node
    ```js
    const element = <h1>Hello, world</h1>;
    ReactDOM.render(element, document.getElementById('root'));
    ```
- React: element, component, props

### Components
- Component names must start with a capital letter. If so, it requires the component to be in the scope

- `props`
- To store internal states, use property `state`
    - Use `this.state = { ... }` in the constructor
    - Use `this.setState({ ... })` everywhere else

- Life Cycle Methods
    - componentDidMount, componentWillMount

- Reading stopped [here](https://reactjs.org/docs/state-and-lifecycle.html#adding-lifecycle-methods-to-a-class)
