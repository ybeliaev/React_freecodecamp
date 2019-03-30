# Render условного выражения из Props

До сих пор вы видели, как использовать if / else, &&, null и тернарный оператор (условие? ExpressionIfTrue: expressionIfFalse) для принятия условных решений о том, что и когда отображать. Однако остается обсудить одну важную тему, которая позволяет объединить любую или все эти концепции с другой мощной функцией React: props. Использование props для условного рендеринга кода очень распространено среди разработчиков React, то есть они используют значение данного prop для автоматического принятия решения о том, что визуализировать.
В этой задаче вы настроите дочерний компонент для принятия решений о рендеринге на основе реквизита. Вы также будете использовать тернарный оператор, но вы можете увидеть, как некоторые другие концепции, которые были рассмотрены в последних нескольких задачах, могут быть столь же полезны в этом контексте.

## задача

Редактор кода имеет два компонента, которые частично определены для вас: родительский элемент с именем GameOfChance и дочерний элемент с именем Results. Они используются для создания простой игры, в которой пользователь нажимает кнопку, чтобы увидеть, выиграют они или проиграют.
Во-первых, вам понадобится простое выражение, которое случайным образом возвращает разные значения при каждом запуске. Вы можете использовать Math.random (). Этот метод возвращает значение от 0 (включительно) до 1 (исключая) при каждом вызове. Так что для шансов 50/50 используйте ```Math.random ()> .5 ```в своем выражении. По статистике, это выражение будет возвращать true в 50% случаев, а false - в остальных 50%. В строке 30 замените комментарий этим выражением, чтобы завершить объявление переменной.
Теперь у вас есть выражение, которое вы можете использовать для принятия случайного решения в коде. Далее вам нужно реализовать это. Визуализируйте компонент Results как дочерний элемент GameOfChance и передайте в выражении как prop под названием fiftyFifty. В компоненте Results напишите тернарное выражение, чтобы отобразить текст «Вы выиграли!» или "Ты проиграл!" основанный на пятидесятидесятидесятимесячной опоре, передаваемой из GameOfChance. Наконец, убедитесь, что метод handleClick () правильно считает каждый ход, чтобы пользователь знал, сколько раз он играл. Это также служит для того, чтобы пользователь знал, что компонент фактически обновлен в случае, если он выигрывает или проигрывает два раза подряд.
```
class Results extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <h1>
      {
        /* change code here */
      }
      </h1>
    )
  };
};

class GameOfChance extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      counter: 1
    }
    this.handleClick = this.handleClick.bind(this);
  }
  handleClick() {
    this.setState({
      counter: 0 // change code here
    });
  }
  render() {
    let expression = null; // change code here
    return (
      <div>
        <button onClick={this.handleClick}>Play Again</button>
        { /* change code below this line */ }

        { /* change code above this line */ }
        <p>{'Turn: ' + this.state.counter}</p>
      </div>
    );
  }
};
```
* Компонент GameOfChance должен существовать и отображаться на странице.
* GameOfChance должен вернуть один элемент кнопки.
* GameOfChance должен вернуть один экземпляр компонента Results, у которого есть prop  с именем fiftyFifty.
* Когда компонент GameOfChance впервые отображается в DOM, должен быть возвращен элемент p с внутренним текстом Turn: 1.
* Каждый раз, когда нажимается кнопка, состояние счетчика должно увеличиваться на значение 1, и в DOM должен быть представлен один элемент p, содержащий текст «Turn: N», где N - это значение состояния счетчика.
* Когда компонент GameOfChance впервые монтируется в DOM, и каждый раз, когда после этого нажимается кнопка, должен возвращаться один элемент h1, который случайным образом отображает либо You Win! или ты проиграл!
```
class Results extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <h1>
      {
        this.props.fiftyFifty
      }
      </h1>
    )
  };
};

class GameOfChance extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      counter: 1
    }
    this.handleClick = this.handleClick.bind(this);
  }
  handleClick() {
  this.setState({
    counter: this.state.counter + 1
  });
}
  render() {
    let expression = Math.random() > .5; // change code here
    return (
      <div>
        <button onClick={this.handleClick}>Play Again</button>
        { /* change code below this line */ }
        {(expression == 1)? <Results fiftyFifty="You win!"/> : <Results fiftyFifty="You lose!"/> }
        { /* change code above this line */ }
        <p>{'Turn: ' + this.state.counter}</p>
      </div>
    );
  }
};
```