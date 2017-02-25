# React-router
React Router keeps the UI in sync with the URL.
> [React-router](https://github.com/ReactTraining/react-router)

## react-router的导入
```JavaScript
import {Router, Route, hashHistory} from 'react-router';
```
## react－router的使用
可以在`render()`使用`<Router>`来描述router的内容。
使用`<Route>`来封装每个组件
```JavaScript
<Router history={hashHistory}>
    <Route component={Index} path="/">
        <Route component={Detail} path="details"></Route>
    </Route>
    <Route component={ComponentList} path="list"></Route>
</Router>
```

## route中的嵌套
在`<Route>`中可以嵌套`<Route>`，以达到共享同一个页面但是有不同的url以及内容的作用。
需要在相应的component的render中在相应位置添加一个参数：
```JavaScript
<div>
    {this.props.children}
</div>
```

## Link组件
通过`<Link>`来添加类似url的属性
```JavaScript
               <ul>
                    <li><Link to={'/'}>首页</Link></li>
                    <li><Link to={'/details'}>详细页面</Link></li>
                    <li><Link to={'/list'}>首页</Link></li>
                </ul>
```


## router中的传参
在router中设置要传的参数
```JavaScript
<Route component={ComponentList} path="list/:id"></Route>
```
在相关的组件中调用接受设定好的参数：
```JavaScript
<p>hello list id: {this.props.params.id}</p>
```
在相应调用了这个组件的link中就可以给他传参：
```JavaScript
<li><Link to={'/list/1234'}>首页</Link></li>
```