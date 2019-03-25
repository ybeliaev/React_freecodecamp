# Установить State  с помощью this.setState

Предыдущие задачи охватывали state компонента и как инициализировать state в constructor. Существует также способ изменить state компонента. React предоставляет метод для обновления state компонента, называемый setState. Вы вызываете метод setState в своем классе компонентов следующим образом: this.setState (), передавая объект с парами ключ-значение. Ключи - это свойства вашего состояния, а значения - обновленные данные о состоянии. Например, если бы мы сохраняли username в state  и хотели обновить его, это выглядело бы так:
```
this.setState({
  username: 'Lewis'
});
```
React ожидает, что вы никогда не будете изменять state напрямую, вместо этого всегда используйте this.setState (), когда происходят изменения состояния. Также следует учесть, что React может пакетно обновлять несколько состояний, чтобы повысить производительность. Это означает, что обновления состояния с помощью метода setState могут быть асинхронными. Существует альтернативный синтаксис для метода setState, который позволяет обойти эту проблему. Это редко требуется, но хорошо иметь это в виду! Пожалуйста, обратитесь к документации React для получения более подробной информации.

## задача

В редакторе кода есть элемент button, который имеет обработчик onClick (). Этот обработчик срабатывает, когда кнопка получает событие нажатия в браузере, и запускает метод handleClick, определенный в MyComponent. В методе handleClick обновите state компонента, используя this.setState (). Установите свойство name в state равным строке React Rocks !.
Нажмите на кнопку и посмотрите обновление состояния визуализации. Не беспокойтесь, если вы не до конца понимаете, как работает код обработчика кликов. Это покрыто в предстоящих задачах.
* The state of MyComponent should initialize with the key value pair { name: Initial State }.
* MyComponent should render an h1 header.
* The rendered h1 header should contain text rendered from the component's state.
* Calling the handleClick method on MyComponent should set the name property in state to equal React Rocks!.
```
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      name: 'Initial State'
    };
    this.handleClick = this.handleClick.bind(this);
  }
  handleClick() {
    // change code below this line

    // change code above this line
  }
  render() {
    return (
      <div>
        <button onClick={this.handleClick}>Click Me</button>
        <h1>{this.state.name}</h1>
      </div>
    );
  }
};
```
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      name: 'Initial State'
    };
    this.handleClick = this.handleClick.bind(this);
  }
  handleClick() {
    // change code below this line
    this.setState({
      name: 'React Rocks!'
    });
    // change code above this line
  }
  render() {
    return (
      <div>
        <button onClick={this.handleClick}>Click Me</button>
        <h1>{this.state.name}</h1>
      </div>
    );
  }
};
```