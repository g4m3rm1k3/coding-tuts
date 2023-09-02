![[Pasted image 20230824040934.png]]

Display a list of elements
```js
ReactDOM.render(
  [<Button/>, <Display/>],
  document.getElementById('mountNode'),
);

```
or
```js
ReactDOM.render(
  <div>
    <Button/>
    <Display/>
  </div>,
  document.getElementById('mountNode'),
);
```
