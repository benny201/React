# React

## 虚拟DOM(Virtual DOM)结构
在APP与传统DOM加了一层Virtual DOM。
虚拟的DOM的核心思想是：对复杂的文档DOM结构，提供一种方便的工具，进行最小化地DOM操作。这句话，也许过于抽象，却基本概况了虚拟DOM的设计思想
两个要点：
* 用JavaScript创建DOM
* 比较两棵虚拟DOM树的差异

### diff算法
在用JS对象表示DOM结构后，当页面状态发生变化而需要操作DOM时，我们可以先通过虚拟DOM计算出对真实DOM的最小修改量，
然后再修改真实DOM结构(因为真实DOM的操作代价太大)。
我们很少跨级别的修改DOM节点，通常是修改节点的属性、调整子节点的顺序、添加子节点等。因此，我们只需要对同级别节点进行比较，避免了diff算法的复杂性。
对同级别的节点进行DFS。


## JSX
```JavaScript
const element = <h1>Hello, world!</h1>;
```
This funny tag syntax is neither a string nor HTML.It is called `JSX`,
and it is a syntax extension to JavaScript(describe what the UI should look like).
```JavaScript
const element = (
  <h1>
    Hello, {formatName(user)}!
  </h1>
);
```
* 传参数需要用{}包裹,类似在web2py的html代码中嵌入python
```Java
By default, React DOM escapes any values embedded in JSX before rendering them.
Thus it ensures that you can never inject anything that's not explicitly written in your application.
Everything is converted to a string before being rendered.
This helps prevent XSS (cross-site-scripting) attacks.
```
* 注释：{/**/}
* The <div /> syntax is transformed at build time to React.createElement('div')



## React elements
React elements are immutable. Once you create an element, you can't change its children or attributes.
An element is like a single frame in a movie: it represents the UI at a certain point in time.
React DOM compares the element and its children to the previous one, and only applies the DOM updates necessary to bring the DOM to the desired state.
* render() 中的return 必须只能是一个节点，但是可以通过外包一个父节点把所有内容包裹起来。
```JavaScript
The render method returns a description of what you want to render, and then React takes that description and renders it to the screen.
In particular, render returns a React element, which is a lightweight description of what to render.
```
* 新创建的类如果外部可以调用，必须加export default


## React components
The simplest way to define a component is to write a JavaScript function:

```JavaScript
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}

const element = <Welcome name="Sara" />;
ReactDOM.render(
  element,
  document.getElementById('root')
);
```
Always start component names with a capital letter.
For example, <div /> represents a DOM tag, but <Welcome /> represents a component and requires Welcome to be in scope.


And the class style:
`Converting a Function to a Class`
```JavaScript
class Welcome extends React.Component {
  render() {
    return <h1>Hello, {this.props.name}</h1>;
  }
}
```
* You can convert a functional component like Clock to a class in five steps:
* Create an ES6 class with the same name that extends React.Component.
* Add a single empty method to it called render().
* Move the body of the function into the render() method.
* Replace props with this.props in the render() body.
* Delete the remaining empty function declaration.




## React pros属性
* pros 和 state同属于一个component
* pros属性是为了在不同component中的交流。
* 属于外来属性
* `this.pros.prosname`
* Whether you declare a component as a function or a class, it must never modify its own props
```JavaScript
function sum(a, b) {
  return a + b;
}
```
## React State
* state 只会管理自身的class, 不污染其他的模块 -> this.state
* 在constructor()中构造this.state
* setState()更新state
* 自身的属性: React components can have state by setting this.state in the constructor, which should be considered private to the component.
* `this.setState()` to schedule updates to the component local state: `Do Not Modify State Directly`


## Handling Events in React
Handling events with React elements is very similar to handling events on DOM elements. There are some syntactic differences:
* React events are named using camelCase, rather than lowercase.
* With JSX you pass a function as the event handler, rather than a string.

```JavaScript
For DOM:
<button onclick="activateLasers()">
  Activate Lasers
</button>
For React:
<button onClick={activateLasers}>
  Activate Lasers
</button>
```

* Another difference is that you cannot return false to prevent default behavior in React. You must call preventDefault explicitly.
```JavaScript
function ActionLink() {
  function handleClick(e) {
    e.preventDefault();
    console.log('The link was clicked.');
  }

  return (
    <a href="#" onClick={handleClick}>
      Click me
    </a>
  );
}
```


### 多组件嵌套
* 分组件创建js




## React的生命周期



