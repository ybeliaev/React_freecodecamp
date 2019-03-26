# Simple Counter

Вы можете разработать более сложный компонент с сохранением состояния, комбинируя концепции, описанные до сих пор. К ним относятся инициализация state, написание методов, которые устанавливают state, и назначение обработчиков щелчков для запуска этих методов.

## задача

Компонент Counter отслеживает значение count в state. Есть две кнопки, которые вызывают методы increment () и decment (). Запишите эти методы, чтобы значение счетчика увеличивалось или уменьшалось на 1 при нажатии соответствующей кнопки. Также создайте метод reset (), чтобы при нажатии кнопки сброса счетчик был равен 0.
Примечание. Убедитесь, что вы не изменяете classNames кнопок. Также не забудьте добавить необходимые привязки для вновь созданных методов в конструкторе.
* Counter should return a div element which contains three buttons with text content in this order Increment!, Decrement!, Reset.
* The state of Counter should initialize with a count property set to 0.
* Clicking the increment button should increment the count by 1.
* Clicking the decrement button should decrement the count by 1.
* Clicking the reset button should reset the count to 0.
```
class Counter extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      count: 0
    };
    // change code below this line

    // change code above this line
  }
  // change code below this line

  // change code above this line
  render() {
    return (
      <div>
        <button className='inc' onClick={this.increment}>Increment!</button>
        <button className='dec' onClick={this.decrement}>Decrement!</button>
        <button className='reset' onClick={this.reset}>Reset</button>
        <h1>Current Count: {this.state.count}</h1>
      </div>
    );
  }
};
```
## решение

```
class Counter extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      count: 0
    };
    // change code below this line
    this.increment = this.increment.bind(this); 
    this.decrement = this.decrement.bind(this);
    this.reset = this.reset.bind(this);
    // change code above this line
  }
  // change code below this line
  increment(){this.setState({count: this.state.count + 1})}
  decrement(){ this.setState({count: this.state.count - 1}) };
  reset(){ this.setState({ count: 0 }) }
  // change code above this line
  render() {
    return (
      <div>
        <button className='inc' onClick={this.increment}>Increment!</button>
        <button className='dec' onClick={this.decrement}>Decrement!</button>
        <button className='reset' onClick={this.reset}>Reset</button>
        <h1>Current Count: {this.state.count}</h1>
      </div>
    );
  }
};
```

# Создать контролируемый Input

Ваше приложение может иметь более сложные взаимодействия между state и отображаемым UI. Например, элементы управления формой для ввода текста, такие как input и textarea, поддерживают свое собственное состояние в DOM как пользовательские типы. С помощью React вы можете перевести это изменяемое состояние в state компонента React. Ввод пользователя становится частью state приложения, поэтому React контролирует значение этого поля ввода. Как правило, если у вас есть компоненты React с полями ввода, в которые пользователь может вводить данные, это будет контролируемая форма ввода.

## задача

```
class ControlledInput extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      input: ''
    };
    // change code below this line

    // change code above this line
  }
  // change code below this line

  // change code above this line
  render() {
    return (
      <div>
        { /* change code below this line */}

        { /* change code above this line */}
        <h4>Controlled Input:</h4>
        <p>{this.state.input}</p>
      </div>
    );
  }
};
```

Редактор кода имеет каркас компонента ControlledInput для создания контролируемого элемента input. state компонента уже инициализировано свойством input, которое содержит пустую строку. Это значение представляет текст, который пользователь вводит в поле input.
Сначала создайте метод handleChange(), у которого есть параметр с именем event. Когда метод вызывается, он получает объект event, который содержит строку текста из элемента ввода. Вы можете получить доступ к этой строке с помощью event.target.value внутри метода. Обновите свойство input state компонента с помощью этой новой строки.
В методе рендеринга создайте элемент input над тегом h4. Добавьте атрибут value, который равен свойству input состояния компонента. Затем добавьте обработчик события onChange(), установленный в метод handleChange().
Когда вы вводите в поле ввода, этот текст обрабатывается методом handleChange (), устанавливается как свойство input в локальном state и отображается как значение в поле state на странице. Состояние state является единственным источником правды относительно входных данных.

И последнее, но не менее важное: не забудьте добавить необходимые привязки в конструктор.
* ControlledInput should return a div element which contains an input and a p tag.
* The state of ControlledInput should initialize with an input property set to an empty string.
* Typing in the input element should update the state and the value of the input, and the p element should render this state as you type.
```
class ControlledInput extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      input: ''
    };
    // change code below this line
    this.handleChange = this.handleChange.bind(this);
    // change code above this line
  }
  // change code below this line
  handleChange(event){
    this.setState({ input: event.target.value })
  };
  // change code above this line
  render() {
    return (
      <div>
        { /* change code below this line */}
        <input value = { this.state.input } onChange = {this.handleChange}/>
        { /* change code above this line */}
        <h4>Controlled Input:</h4>
        <p>{this.state.input}</p>
      </div>
    );
  }
};
```
