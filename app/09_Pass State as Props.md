# Передать состояние в качестве props дочерним компонентам

Вы видели множество примеров, которые передавали реквизиты дочерним элементам JSX и дочерним компонентам React в предыдущих задачах. Вы можете быть удивлены, откуда взялись эти props. Обычным шаблоном является наличие компонента с состоянием, содержащего state, важное для вашего приложения, который затем отображает дочерние компоненты. Вы хотите, чтобы эти компоненты имели доступ к некоторым частям этого state, которые передаются как props.

Например, может быть, у вас есть компонент App, который отображает Navbar, среди других компонентов. В вашем приложении у вас есть state, которое содержит много информации о пользователе, но Navbar нужен только доступ к имени пользователя, чтобы он мог отображать его. Вы передаете этот кусок state компоненту Navbar в качестве реквизита.

Эта модель иллюстрирует некоторые важные парадигмы в React. Первый - это однонаправленный поток данных(unidirectional data flow). Состояние перемещается в одном направлении вниз по дереву компонентов вашего приложения, от родительского компонента с сохранением состояния до дочерних компонентов. Дочерние компоненты получают только те данные о состоянии, которые им необходимы. Во-вторых, сложные приложения с состоянием можно разбить на несколько или, может быть, один компонент с состоянием. Остальные компоненты просто получают состояние от родителя в качестве реквизита и отображают пользовательский интерфейс из этого состояния. Он начинает создавать разделение, в котором управление состоянием выполняется в одной части кода, а визуализация пользовательского интерфейса - в другой. Этот принцип отделения логики состояния от логики пользовательского интерфейса является одним из ключевых принципов React. При правильном использовании это значительно упрощает управление сложными приложениями с сохранением состояния.

## задача

Компонент MyApp с состоянием и отображает компонент Navbar как дочерний. Передайте свойство name в его состоянии до дочернего компонента, затем покажите имя в теге h1, который является частью метода рендеринга Navbar.

```
class MyApp extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      name: 'CamperBot'
    }
  }
  render() {
    return (
       <div>
         <Navbar /* your code here */ />
       </div>
    );
  }
};

class Navbar extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
    <div>
      <h1>Hello, my name is: /* your code here */ </h1>
    </div>
    );
  }
};
```
* The MyApp component should render with a Navbar component inside.
* The Navbar component should receive (получать) the MyApp state property name as props.
* The h1 element in Navbar should render the name prop.
```
class MyApp extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      name: 'CamperBot'
    }
  }
  render() {
    return (
       <div>
         <Navbar name = {this.state.name} />
       </div>
    );
  }
};

class Navbar extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
    <div>
      <h1>Hello, my name is: {this.props.name} </h1>
    </div>
    );
  }
};
```

# Прокинуть  Callback как  Props

Вы можете передавать state как props дочерним компонентам, но вы не ограничены передачей данных. Вы также можете передать функции-обработчики или любой метод, определенный в компоненте React, в дочерний компонент. Это позволяет дочерним компонентам взаимодействовать с их родительскими компонентами. Вы передаете методы ребенку, как обычная prop. Ему присвоено имя, и у вас есть доступ к этому имени метода в this.props дочернего компонента.
## задача

В редакторе кода есть три компонента. Компонент MyApp является родительским, который будет отображать дочерние компоненты GetInput и RenderInput. Добавьте компонент GetInput к методу рендеринга в MyApp, затем передайте ему prop, называемый input, назначенный для inputValue из state MyApp. Также создайте prop с именем handleChange и передайте ему обработчик ввода handleChange.
Затем добавьте RenderInput к методу рендеринга в MyApp, затем создайте prop с именем input и передайте ему inputValue из state. Как только вы закончите, вы сможете ввести поле ввода в компоненте GetInput, который затем вызывает метод-обработчик в его родительском элементе через props. Это обновляет входные данные в state родителя, которые передаются как props для обоих потомков. Наблюдайте, как данные передаются между компонентами и как единственным источником правды остается state родительского компонента. Следует признать, что этот пример немного надуман, но должен служить иллюстрацией того, как данные и обратные вызовы могут передаваться между компонентами React.
```
class MyApp extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      inputValue: ''
    }
    this.handleChange = this.handleChange.bind(this);
  }
  handleChange(event) {
    this.setState({
      inputValue: event.target.value
    });
  }
  render() {
    return (
       <div>
        { /* change code below this line */ }

        { /* change code above this line */ }
       </div>
    );
  }
};

class GetInput extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h3>Get Input:</h3>
        <input
          value={this.props.input}
          onChange={this.props.handleChange}/>
      </div>
    );
  }
};

class RenderInput extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h3>Input Render:</h3>
        <p>{this.props.input}</p>
      </div>
    );
  }
};
```
## решение

```
class MyApp extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      inputValue: ''
    }
    this.handleChange = this.handleChange.bind(this);
  }
  handleChange(event) {
    this.setState({
      inputValue: event.target.value
    });
  }
  render() {
    return (
       <div>
        { /* change code below this line */ 
        <GetInput input={this.state.inputValue} handleChange={this.handleChange}/>
        }
        { /* change code above this line */ 
        <RenderInput input={this.state.inputValue}/>
        }
       </div>
    );
  }
};
....etc
```