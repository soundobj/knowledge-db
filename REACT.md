# Table of Contents
- [Reconciliation](#reconciliation)
- [Hooks](#hooks)
- [State](#state-hook)
- [Effect](#effect-hook)
- [LifeCycleCallbacks](#lifecycle)
- [props.render](#propsrender)

## Reconciliation <a name="reconciliation"></a>
React implements its DOM reconciliation algorithm based on two assumptions:
- Two elements of different types will produce different trees.<br />
- When comparing two react DOM elements of the same type React looks at the atttributes of both keeps the same underlying DOM node and only updates  the changed attributed such as the class name for example.<br />
- The developer can hint at which child elements may be stable across different renders with a key prop.<br />
- When children have keys, React uses the key to match children in the original tree with the children in the subsequent tree. this is useful for improving reconciliation performance when a node changes at the top of a long list of sibblings. the key has to be unique among its siblings not globally unique. the key has to be unique among its siblings not globally unique.<br />

## Hooks <a  name="hooks"></a>
- Hooks allow you to reuse stateful logic without changing your component hierarchy.<br />
- Hooks let you split one component into smaller functions based on what pieces are related (such as setting up a subscription or fetching data), rather than forcing a split based on lifecycle methods. (Effect Hook) <br />
- Hooks let you use more of React’s features without classes.<br />

## State <a name="state-hook"></a>
If you write a function component and realize you need to add some state to it, previously you had to convert it to a class. Now you can use a Hook inside the existing function component.<br />

```
 const [count, setCount] = useState(0);
```
What does useState return? It returns a pair of values: the current state and a function that updates it. This is why we write 
```
const [count, setCount] = useState()
```
## Effect <a name="effect-hook"></a>
- You can think of useEffect Hook as componentDidMount, componentDidUpdate, and componentWillUnmount combined.<br />
- By using this Hook, you tell React that your component needs to do something after render. React will remember the function you passed (we’ll refer to it as our “effect”), and call it later after performing the DOM updates. In this effect, we set the document title, but we could also perform data fetching or call some other imperative API.<br />
 - Unlike componentDidMount or componentDidUpdate, effects scheduled with useEffect don’t block the browser from updating the screen. This makes your app feel more responsive. The majority of effects don’t need to happen synchronously.<br />
- When we returning a function from our effect is the optional cleanup mechanism for effects. Every effect may return a function that cleans up after it. This lets us keep the logic for adding and removing subscriptions close to each other. They’re part of the same effect!<br />

## LifeCycle callbacks <a name="lifecycle"></a>
- **getDerivedStateFromProps()** is invoked right before calling the render method, both on the initial mount and on subsequent updates. It should return an object to update the state, or null to update nothing.<br /> 
- **getSnapshotBeforeUpdate()** is invoked right before the most recently rendered output is committed to e.g. the DOM. It enables your component to capture some information from the DOM (e.g. scroll position) before it is potentially changed.

## Props render <a name="propsrender"></a>
- a render prop is a function prop that a component uses to know what to render.<br />
- This technique makes the behavior that we need to share extremely portable<br />
```
class Mouse extends React.Component {
  constructor(props) {
    super(props);
    this.handleMouseMove = this.handleMouseMove.bind(this);
    this.state = { x: 0, y: 0 };
  }

  handleMouseMove(event) {
    this.setState({
      x: event.clientX,
      y: event.clientY
    });
  }

  render() {
    return (
      <div style={{ height: '100%' }} onMouseMove={this.handleMouseMove}>

        {/*
          Instead of providing a static representation of what <Mouse> renders,
          use the `render` prop to dynamically determine what to render.
        */}
        {this.props.render(this.state)}
      </div>
    );
  }
}
class MouseTracker extends React.Component {
  render() {
    return (
      <div>
        <h1>Move the mouse around!</h1>
        <Mouse render={mouse => (
          <Cat mouse={mouse} />
        )}/>
      </div>
    );
  }
}
```

<!-- -->
- This pattern removes most of the issues around mixings and HOCs namely:
- ES6 classes. Yep, not a problem. We can use render props with components that are created using ES6 classes.<br />
- Indirection. We don’t have to wonder where our state or props are coming from. We can see them in the render prop’s argument list.<br />
- Naming collisions. There is no automatic merging of property names, so there is no chance for a naming collision.<br />
