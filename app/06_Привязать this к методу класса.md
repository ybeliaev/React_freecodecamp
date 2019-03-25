# Bind 'this' to a Class Method

Помимо установки и обновления state, вы также можете определить методы для класса вашего компонента. Метод класса обычно должен использовать ключевое слово this, чтобы он мог обращаться к свойствам класса (таким как state и props) внутри области действия метода. Есть несколько способов разрешить вашим методам класса доступ к this.

Одним из распространенных способов является явное связывание this в конструкторе, так что this становится связанным с методами класса, когда компонент инициализируется.
Возможно, вы заметили, что последний вызов использовал ```this.handleClick = this.handleClick.bind(this)``` для его метода handleClick в конструкторе. Затем, когда вы вызываете функцию, подобную this.setState() внутри вашего метода класса, this относится к классу и не будет undefined.
Примечание. Ключевое слово this является одним из самых запутанных аспектов JavaScript, но оно играет важную роль в React. Хотя его поведение здесь совершенно нормальное, эти уроки не являются местом для углубленного изучения this, поэтому, пожалуйста, обратитесь к другим урокам, если вышеупомянутое сбивает с толку!

## задача
Редактор кода имеет компонент с state, которое отслеживает количество элементов. У него также есть метод, который позволяет увеличивать это количество элементов. Однако метод не работает, потому что он использует ключевое слово this, которое не определено. Исправьте это, явно связав this с методом addItem() в конструкторе компонента.
Затем добавьте обработчик щелчка к элементу button в методе рендеринга. Он должен вызывать метод addItem(), когда кнопка получает событие нажатия. Помните, что метод, который вы передаете обработчику onClick, нуждается в фигурных скобках, потому что он должен интерпретироваться непосредственно как JavaScript.
* MyComponent should return a div element which wraps two elements, a button and an h1 element, in that order.
* The state of MyComponent should initialize with the key value pair { itemCount: 0 }.
* Clicking the button element should run the addItem method and increment the state itemCount by 1.
```
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      itemCount: 0
    };
    // change code below this line

    // change code above this line
  }
  addItem() {
    this.setState({
      itemCount: this.state.itemCount + 1
    });
  }
  render() {
    return (
      <div>
        { /* change code below this line */ }
        <button>Click Me</button>
        { /* change code above this line */ }
        <h1>Current Item Count: {this.state.itemCount}</h1>
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
      itemCount: 0
    };
    // change code below this line
    this.addItem = this.addItem.bind(this);
    // change code above this line
  }
  addItem() {
    this.setState({
      itemCount: this.state.itemCount + 1
    });
  }
  render() {
    return (
      <div>
        { /* change code below this line */ }
        <button onClick={this.addItem}>Click Me</button>
        { /* change code above this line */ }
        <h1>Current Item Count: {this.state.itemCount}</h1>
      </div>
    );
  }
}
```
или

```
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      itemCount: 0
    };
    
  }
  addItem() {
    this.setState({
      itemCount: this.state.itemCount + 1
    });
  }
  render() {
    return (
      <div>
        { /* change code below this line */ }
        <button onClick={()=>this.addItem()}>Click Me</button>
        { /* change code above this line */ }
        <h1>Current Item Count: {this.state.itemCount}</h1>
      </div>
    );
  }
};
```