# Оптимизация повторного рендеринга с shouldComponentUpdate

До сих пор, если какой-либо компонент получает новое состояние или новый props, он перерисовывает себя и всех своих потомков. Обычно это нормально. Но React предоставляет метод жизненного цикла, который вы можете вызывать, когда дочерние компоненты получают новое состояние или props, и конкретно объявлять, должны ли компоненты обновляться или нет. Это метод shouldComponentUpdate(), и он принимает в качестве параметров nextProps и nextState.

Этот метод является полезным способом оптимизации производительности. Например, поведение по умолчанию заключается в том, что ваш компонент перерисовывается при получении новых props, даже если props не изменились. Вы можете использовать shouldComponentUpdate(), чтобы предотвратить это, сравнивая props. Метод должен возвращать логическое значение, которое сообщает React, обновлять компонент или нет. Вы можете сравнить текущие props (this.props) со следующими props (nextProps), чтобы определить, нужно ли вам обновить или нет, и вернуть соответственно true или false.

## задача

Метод shouldComponentUpdate() добавляется в компонент с именем OnlyEvens. В настоящее время этот метод возвращает true, поэтому OnlyEvens перерисовывает каждый раз, когда получает новые реквизиты. Измените метод так, чтобы OnlyEvens обновлялся, только если значение его нового props является четным. Нажмите кнопку «Добавить» и наблюдайте за порядком событий в консоли вашего браузера, когда запускаются другие хуки жизненного цикла.
```
class OnlyEvens extends React.Component {
  constructor(props) {
    super(props);
  }
  shouldComponentUpdate(nextProps, nextState) {
    console.log('Should I update?');
     // change code below this line
    return true;
     // change code above this line
  }
  componentWillReceiveProps(nextProps) {
    console.log('Receiving new props...');
  }
  componentDidUpdate() {
    console.log('Component re-rendered.');
  }
  render() {
    return <h1>{this.props.value}</h1>
  }
};

class Controller extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      value: 0
    };
    this.addValue = this.addValue.bind(this);
  }
  addValue() {
    this.setState({
      value: this.state.value + 1
    });
  }
  render() {
    return (
      <div>
        <button onClick={this.addValue}>Add</button>
        <OnlyEvens value={this.state.value}/>
      </div>
    );
  }
};
```
* The Controller component should render the OnlyEvens component as a child.
* The shouldComponentUpdate method should be defined on the OnlyEvens component.
* The OnlyEvens component should return an h1 tag which renders the value of this.props.value.
* OnlyEvens should re-render only when nextProps.value is even.
```
class OnlyEvens extends React.Component {
  constructor(props) {
    super(props);
  }
  shouldComponentUpdate(nextProps, nextState) {
    console.log('Should I update?');
     // change code below this line
      if (nextProps.value % 2 == 0) {
        return true;
      }
      return false;
     // change code above this line
  }
  componentWillReceiveProps(nextProps) {
    console.log('Receiving new props...');
  }
  componentDidUpdate() {
    console.log('Component re-rendered.');
  }
  render() {
    return <h1>{this.props.value}</h1>
  }
};

class Controller extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      value: 0
    };
    this.addValue = this.addValue.bind(this);
  }
  addValue() {
    this.setState({
      value: this.state.value + 1
    });
  }
  render() {
    return (
      <div>
        <button onClick={this.addValue}>Add</button>
        <OnlyEvens value={this.state.value}/>
      </div>
    );
  }
};
```
Для этого решения вы будете использовать оператор if / then, чтобы проверить, является ли значение nextProps четным. nextProps отличается от props тем, что это значение, которое еще не отображалось в пользовательском интерфейсе, поэтому в методе shouldComponentUpdate () вы, по сути, запрашиваете разрешение обновить пользовательский интерфейс значением nextProps.