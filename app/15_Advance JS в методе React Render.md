# Advance JS в методе React Render

В предыдущих выпусках вы узнали, как внедрить код JavaScript в код JSX с помощью фигурных скобок {}, для таких задач, как доступ к props, передача props, доступ к state, вставка комментариев в код и, совсем недавно, стилизация компонентов. Все это общие случаи использования JavaScript в JSX, но они не единственный способ использования кода JavaScript в ваших компонентах React.
Вы также можете написать JavaScript непосредственно в ваших методах рендеринга перед оператором return, НЕ вставляя его в фигурные скобки. Это потому, что это еще не в коде JSX. Когда вы захотите позже использовать переменную в коде JSX внутри оператора return, вы поместите имя переменной в фигурные скобки.

## задача

В представленном коде метод рендеринга имеет массив, который содержит 20 фраз для представления ответов, найденных в классической игрушке 1980-х годов «Волшебный шар». Событие нажатия кнопки связано с методом ask, поэтому каждый раз, когда нажимается кнопка, генерируется случайное число, которое сохраняется в виде randomIndex в состоянии. В строке 52 удалите строку "change me!" и переназначить answer const, чтобы ваш код случайным образом обращался к possibleAnswers массива возможных ответных действий при каждом обновлении компонента. Наконец, вставьте const answer в теги p.

```
const inputStyle = {
  width: 235,
  margin: 5
}

class MagicEightBall extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      userInput: '',
      randomIndex: ''
    }
    this.ask = this.ask.bind(this);
    this.handleChange = this.handleChange.bind(this);
  }
  ask() {
    if (this.state.userInput) {
      this.setState({
        randomIndex: Math.floor(Math.random() * 20),
        userInput: ''
      });
    }
  }
  handleChange(event) {
    this.setState({
      userInput: event.target.value
    });
  }
  render() {
    const possibleAnswers = [
      'It is certain',
      'It is decidedly so',
      'Without a doubt', 
      'Yes, definitely',
      'You may rely on it',
      'As I see it, yes',
      'Outlook good',
      'Yes',
      'Signs point to yes',
      'Reply hazy try again',
      'Ask again later',
      'Better not tell you now',
      'Cannot predict now',
      'Concentrate and ask again',
      'Don\'t count on it', 
      'My reply is no',
      'My sources say no',
      'Most likely',
      'Outlook not so good',
      'Very doubtful'
    ];
    const answer = 'change me!' // << change code here
    return (
      <div>
        <input
          type="text"
          value={this.state.userInput}
          onChange={this.handleChange}
          style={inputStyle} /><br />
        <button onClick={this.ask}>
          Ask the Magic Eight Ball!
        </button><br />
        <h3>Answer:</h3>
        <p>
          { /* change code below this line */ }

          { /* change code above this line */ }
        </p>
      </div>
    );
  }
};
```
* The MagicEightBall component should exist and should render to the page.
* MagicEightBall's first child should be an input element.
* MagicEightBall's third child should be a button element.
* MagicEightBall's state should be initialized with a property of userInput and a property of randomIndex both set to a value of an empty string.
* When MagicEightBall is first mounted to the DOM, it should return an empty p element.
* When text is entered into the input element and the button is clicked, the MagicEightBall component should return a p element that contains a random element from the possibleAnswers array.

```
const inputStyle = {
  width: 235,
  margin: 5
}

class MagicEightBall extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      userInput: '',
      randomIndex: ''
    }
    this.ask = this.ask.bind(this);
    this.handleChange = this.handleChange.bind(this);
  }
  ask() {
    if (this.state.userInput) {
      this.setState({
        randomIndex: Math.floor(Math.random() * 20),
        userInput: ''
      });
    }
  }
  handleChange(event) {
    this.setState({
      userInput: event.target.value
    });
  }
  render() {
    const possibleAnswers = [
      'It is certain',
      'It is decidedly so',
      'Without a doubt', 
      'Yes, definitely',
      'You may rely on it',
      'As I see it, yes',
      'Outlook good',
      'Yes',
      'Signs point to yes',
      'Reply hazy try again',
      'Ask again later',
      'Better not tell you now',
      'Cannot predict now',
      'Concentrate and ask again',
      'Don\'t count on it', 
      'My reply is no',
      'My sources say no',
      'Most likely',
      'Outlook not so good',
      'Very doubtful'
    ];
    const answer = possibleAnswers[this.state.randomIndex] // << change code here
    return (
      <div>
        <input
          type="text"
          value={this.state.userInput}
          onChange={this.handleChange}
          style={inputStyle} /><br />
        <button onClick={this.ask}>
          Ask the Magic Eight Ball!
        </button><br />
        <h3>Answer:</h3>
        <p>
          { /* change code below this line */ }
          {answer}
          { /* change code above this line */ }
        </p>
      </div>
    );
  }
};
```
Пока вы находитесь внутри метода render, а не внутри метода return, вы можете писать JavaScript, не заключая его в фигурные скобки. 
Во-первых, вам нужно установить constant «answer» для значения. Получите доступ к массиву ‘possibleAnswers’ , используя значение randomIndex, которое находится в состоянии вашего компонента. Помните, что вы получаете доступ к состоянию с помощью this.state.