# Использование Array.map() в динамическом Render элементов

Условный рендеринг полезен, но вам могут понадобиться ваши компоненты для рендеринга неизвестного количества элементов. Часто в реактивном программировании у программиста нет возможности узнать, в каком состоянии находится приложение, до времени выполнения, потому что многое зависит от взаимодействия пользователя с этой программой. Программисты должны написать свой код, чтобы правильно обрабатывать это неизвестное состояние заранее. Использование Array.map() в React иллюстрирует эту концепцию.
Например, вы создаете простое приложение «Список дел». Как программист, вы не можете знать, сколько элементов пользователь может иметь в своем списке. Вам необходимо настроить свой компонент для динамического отображения правильного количества элементов списка задолго до того, как кто-то, использующий программу, решит, что сегодня день стирки.
```
const textAreaStyles = {
  width: 235,
  margin: 5
};

class MyToDoList extends React.Component {
  constructor(props) {
    super(props);
    // change code below this line

    // change code above this line
    this.handleSubmit = this.handleSubmit.bind(this);
    this.handleChange = this.handleChange.bind(this);
  }
  handleSubmit() {
    const itemsArray = this.state.userInput.split(',');
    this.setState({
      toDoList: itemsArray
    });
  }
  handleChange(e) {
    this.setState({
      userInput: e.target.value
    });
  }
  render() {
    const items = null; // change code here
    return (
      <div>
        <textarea
          onChange={this.handleChange}
          value={this.state.userInput}
          style={textAreaStyles}
          placeholder="Separate Items With Commas" /><br />
        <button onClick={this.handleSubmit}>Create List</button>
        <h1>My "To Do" List:</h1>
        <ul>
          {items}
        </ul>
      </div>
    );
  }
};
```
Редактор кода имеет большую часть настроенного компонента MyToDoList. Часть этого кода должна выглядеть знакомо, если вы выполнили контролируемый вызов формы. Вы заметите textarea и button, а также несколько методов, которые отслеживают их состояния, но на странице еще ничего не отображается.

Внутри constructor создайте объект this.state и определите два состояния: userInput следует инициализировать как пустую строку, а toDoList - как пустой массив. Затем удалите комментарий в методе render() рядом с переменной items. Вместо этого отобразите массив toDoList, хранящийся во внутреннем состоянии компонента, и динамически отобразите li для каждого элемента. Попробуйте ввести строку eat, code, sleep в textarea, затем нажмите кнопку и посмотрите, что произойдет.
Примечание. Возможно, вы знаете, что все дочерние элементы-братья и сестры, созданные с помощью такой операции сопоставления, должны быть снабжены уникальным атрибутом ключа. Не волнуйтесь, это тема следующего вызова.
* The MyToDoList component should exist and render to the page.
* The first child of MyToDoList should be a textarea element.
* The third child of MyToDoList should be a button element.
* The state of MyToDoList should be initialized with toDoList as an empty array.
* The state of MyToDoList should be initialized with userInput as an empty string.
* When the Create List button is clicked, the MyToDoList component should dynamically return an unordered list that contains a list item element for every item of a comma-separated list entered into the textarea element.

## finish

```
const textAreaStyles = {
  width: 235,
  margin: 5
};

class MyToDoList extends React.Component {
  constructor(props) {
    super(props);
    // change code below this line
    this.state = {
       toDoList: [],
       userInput: ''
    }
    // change code above this line
    this.handleSubmit = this.handleSubmit.bind(this);
    this.handleChange = this.handleChange.bind(this);
  }
  handleSubmit() {
    const itemsArray = this.state.userInput.split(',');
    this.setState({
      toDoList: itemsArray
    });
  }
  handleChange(e) {
    this.setState({
      userInput: e.target.value
    });
  }
  render() {
    const items = this.state.toDoList.map((item)=>{
      return (<li>{item}</li>)
    }); // change code here
    return (
      <div>
        <textarea
          onChange={this.handleChange}
          value={this.state.userInput}
          style={textAreaStyles}
          placeholder="Separate Items With Commas" /><br />
        <button onClick={this.handleSubmit}>Create List</button>
        <h1>My "To Do" List:</h1>
        <ul>
          {items}
        </ul>
      </div>
    );
  }
};
```