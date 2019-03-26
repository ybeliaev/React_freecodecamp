# Создать контролируемую форму

Последняя проблема показала, что React может контролировать внутреннее состояние определенных элементов, таких как input и textarea, что делает их контролируемыми компонентами. Это относится и к другим элементам формы, включая обычный элемент формы HTML.

## задача

Компонент MyForm настроен с пустой формой с обработчиком отправки(submit handler). Обработчик отправки будет вызван при отправке формы. 
Мы добавили кнопку, которая отправляет форму. Вы можете видеть, что у него установлен type submit, указывающий, что это кнопка, управляющая формой. Добавьте элемент input в form и установите его value и атрибуты onChange(), как в последнем вызове. Затем необходимо завершить метод handleSubmit, чтобы он устанавливал свойство состояния компонента, соответствующее текущему входному значению в локальном state. 
Примечание: Вы также должны вызвать event.preventDefault () в обработчике отправки, чтобы предотвратить поведение отправки формы по умолчанию, которое обновит веб-страницу. 
Наконец, создайте тег h1 после формы, который отображает значение отправки из state компонента. Затем вы можете ввести форму и щелкнуть кнопку (или нажать клавишу ввода), и вы должны увидеть свои данные, отображаемые на странице.

```
class MyForm extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      input: '',
      submit: ''
    };
    this.handleChange = this.handleChange.bind(this);
    this.handleSubmit = this.handleSubmit.bind(this);
  }
  handleChange(event) {
    this.setState({
      input: event.target.value
    });
  }
  handleSubmit(event) {
    // change code below this line

    // change code above this line
  }
  render() {
    return (
      <div>
        <form onSubmit={this.handleSubmit}>
          { /* change code below this line */ }

          { /* change code above this line */ }
          <button type='submit'>Submit!</button>
        </form>
        { /* change code below this line */ }

        { /* change code above this line */ }
      </div>
    );
  }
};
```
* MyForm should return a div element which contains a form and an h1 tag. The form should include an input and a button.
* The state of MyForm should initialize with input and submit properties, both set to empty strings.
* Typing in the input element should update the input property of the component's state.
* Submitting the form should run handleSubmit which should set the submit property in state equal to the current input.
* The h1 header should render the value of the submit field from the component's state.

```
class MyForm extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      input: '',
      submit: '',
    };
    this.handleChange = this.handleChange.bind(this);
    this.handleSubmit = this.handleSubmit.bind(this);
  }
  handleChange(event) {
    this.setState({
      input: event.target.value
    });
  }
  handleSubmit(event) {
    // change code below this line
    event.preventDefault();
    this.setState({
      input: '',
      submit: this.state.input
    })

    // change code above this line
  }
  render() {
    return (
      <div>
        <form onSubmit={this.handleSubmit}>
          { /* change code below this line */ }
          <input value={this.state.input} onChange={this.handleChange}/>
          { /* change code above this line */ }
          <button type='submit'>Submit!</button>
        </form>
        { /* change code below this line */ }
        <h1>Input: {this.state.input} <br /> Submit: {this.state.submit}</h1>
        { /* change code above this line */ }
      </div>
    );
  }
};
```