# Изменение встроенного CSS (inline styles )на основе state компонента

На данный момент вы видели несколько приложений условного рендеринга и использования встроенных стилей. Вот еще один пример, который объединяет обе эти темы. Вы также можете визуализировать CSS в зависимости от state компонента React. Для этого вы проверяете условие и, если оно выполняется, вы изменяете объект стилей, назначенный элементам JSX в методе рендеринга.
Эта парадигма важна для понимания, поскольку она резко отличается от более традиционного подхода к применению стилей путем непосредственного изменения элементов DOM (что, например, очень часто встречается в jQuery). При таком подходе вы должны отслеживать, когда элементы изменяются, а также напрямую обрабатывать фактические манипуляции. Отслеживать изменения может быть сложно, что может сделать ваш пользовательский интерфейс непредсказуемым. Когда вы устанавливаете объект стиля на основе условия, вы описываете, как пользовательский интерфейс должен выглядеть как функция состояния приложения. Существует четкий поток информации, которая движется только в одном направлении. Это предпочтительный метод при написании приложений с помощью React.

## task

Редактор кода имеет простой управляемый компонент input со стилизованной рамкой. Вы хотите оформить эту рамку красным, если пользователь вводит более 15 символов текста в поле ввода. Добавьте условие, чтобы проверить это, и, если условие допустимо, установите стиль границы ввода на ```3px solid red```. Вы можете попробовать это, введя текст в поле ввода.
```
class GateKeeper extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      input: ''
    };
    this.handleChange = this.handleChange.bind(this);
  }
  handleChange(event) {
    this.setState({ input: event.target.value })
  }
  render() {
    let inputStyle = {
      border: '1px solid black'
    };
    // change code below this line

    // change code above this line
    return (
      <div>
        <h3>Don't Type Too Much:</h3>
        <input
          type="text"
          style={inputStyle}
          value={this.state.input}
          onChange={this.handleChange} />
      </div>
    );
  }
};
```
* The GateKeeper component should render a div element.
* The GateKeeper component should be initialized with a state key input set to an empty string.
* The GateKeeper component should render an h3 tag and an input tag.
* The input tag should initially have a style of 1px solid black for the border property.
* The input tag should be styled with a border of 3px solid red if the input value in state is longer than 15 characters.
```
class GateKeeper extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      input: ''
    };
    this.handleChange = this.handleChange.bind(this);
  }
  handleChange(event) {
    this.setState({ input: event.target.value })
  }
  render() {
    let inputStyle = {
      border: '1px solid black'
    };
    // change code below this line
    if(this.state.input.length > 15){
      inputStyle.border = '3px solid red';
    }
    // change code above this line
    return (
      <div>
        <h3>Don't Type Too Much:</h3>
        <input
          type="text"
          style={inputStyle}
          value={this.state.input}
          onChange={this.handleChange} />
      </div>
    );
  }
};
```
