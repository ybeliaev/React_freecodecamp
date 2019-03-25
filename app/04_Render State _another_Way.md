# Render State in the User Interface Another Way

Существует другой способ доступа к state в компоненте. В методе render () перед оператором return вы можете написать JavaScript напрямую. Например, вы можете объявить функции, получить доступ к данным из  state или props, выполнить вычисления для этих данных и так далее. Затем вы можете назначить любые данные переменным, к которым у вас есть доступ в операторе return.

## задача

В методе render  MyComponent определите const с именем name и установите его равным значению name в state компонента. Поскольку вы можете писать JavaScript непосредственно в этой части кода, вам не нужно заключать эту ссылку в фигурные скобки.
Затем, в операторе return, отобразите это значение в теге h1, используя имя переменной. Помните, что вы должны использовать синтаксис JSX (фигурные скобки для JavaScript) в операторе return.
### шаги
* MyComponent should have a key name with value freeCodeCamp stored in its state.
* MyComponent should render an h1 header enclosed in a single div.
* The rendered h1 tag should include a reference to {name}.
* The rendered h1 header should contain text rendered from the component's state.
```
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      name: 'freeCodeCamp'
    }
  }
  render() {
    // change code below this line

    // change code above this line
    return (
      <div>
        { /* change code below this line */ }

        { /* change code above this line */ }
      </div>
    );
  }
};
```
## решение

```
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      name: 'freeCodeCamp'
    }
  }
  render() {
    // change code below this line
    const name = this.state.name;
    // change code above this line
    return (
      <div>
        { /* change code below this line */ }
          <h1>{name}</h1>
        { /* change code above this line */ }
      </div>
    );
  }
};
```

