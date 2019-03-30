# Render with an If/Else 

Другое применение использования JavaScript для управления отображаемым представлением - это привязка элементов, отображаемых к условию. Когда условие истинно, один вид отображается. Когда это ложно, это другой взгляд. Вы можете сделать это с помощью стандартного оператора if / else в методе render() компонента React.

## задача

```MyComponent``` содержит логическое значение в своем state, которое отслеживает, хотите ли вы отображать какой-либо элемент в пользовательском интерфейсе или нет. Кнопка переключает состояние этого значения. В настоящее время каждый раз отображается один и тот же интерфейс. Перепишите метод render () с помощью оператора if / else, чтобы при display = true было возвращено текущее значение разметки. В противном случае верните разметку без элемента h1.
Примечание: вы должны написать if / else, чтобы пройти тесты. Использование троичного оператора здесь не пройдет.
```
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      display: true
    }
    this.toggleDisplay = this.toggleDisplay.bind(this);
  }
  toggleDisplay() {
    this.setState({
      display: !this.state.display
    });
  }
  render() {
    // change code below this line

    return (
       <div>
         <button onClick={this.toggleDisplay}>Toggle Display</button>
         <h1>Displayed!</h1>
       </div>
    );
  }
};
```
* MyComponent should exist and render.
* When display is set to true, a div, button, and h1 should render.
* When display is set to false, only a div and button should render.
* The render method should use an if/else statement to check the condition of this.state.display.
```
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      display: true
    }
    this.toggleDisplay = this.toggleDisplay.bind(this);
  }
  toggleDisplay() {
    this.setState({
      display: !this.state.display
    });
  }
  render() {
    // change code below this line
    if (this.state.display === true){
      return (
       <div>
         <button onClick={this.toggleDisplay}>Toggle Display</button>
         <h1>Displayed!</h1>
       </div>
      );
    }else {
            return (
              <div>
                <button onClick={this.toggleDisplay}>Toggle Display</button>
              </div>
            )
    }
        
  }
};
```
# Использование && для более краткого условия

Операторы if / else работали в последней задаче, но есть более краткий способ достижения того же результата. Представьте, что вы отслеживаете несколько условий в компоненте и хотите, чтобы различные элементы отображались в зависимости от каждого из этих условий. Если вы пишете много других операторов if, которые возвращают немного разные пользовательские интерфейсы, вы можете повторить код, который оставляет место для ошибки. Вместо этого вы можете использовать логический оператор && для выполнения условной логики более кратким способом. Это возможно, потому что вы хотите проверить, является ли условие истинным, и если это так, вернуть некоторую разметку. Вот пример:
```{condition && <p>markup</p>}```
Если condition = true, разметка будет возвращена. Если условие ложно, операция немедленно вернет ложь после оценки условия и ничего не вернет. Вы можете включить эти операторы непосредственно в ваш JSX и объединить несколько условий, написав && после каждого. Это позволяет вам обрабатывать более сложную условную логику в вашем методе render () без повторения большого количества кода.

## задача
Решите предыдущий пример еще раз, чтобы h1 отображал только если display true, но вместо логического оператора if / else используйте логический оператор &&.
```
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      display: true
    }
    this.toggleDisplay = this.toggleDisplay.bind(this);
  }
  toggleDisplay() {
    this.setState({
      display: !this.state.display
    });
  }
  render() {
    // change code below this line
    return (
       <div>
         <button onClick={this.toggleDisplay}>Toggle Display</button>
         {this.state.display && <h1>Displayed!</h1>}
       </div>
    );
  }
};
```