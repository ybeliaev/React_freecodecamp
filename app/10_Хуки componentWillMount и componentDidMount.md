# Метод жизненного цикла componentWillMount()

У компонентов React есть несколько специальных методов, которые предоставляют возможность выполнять действия в определенных точках жизненного цикла компонента. Это так называемые методы жизненного цикла, или ловушки жизненного цикла, которые позволяют перехватывать компоненты в определенные моменты времени. Это может происходить до того, как они будут отрисованы, до их обновления, до того, как они получат реквизиты, до их размонтирования и т. Д. Вот список некоторых основных методов жизненного цикла:
```
componentWillMount()

componentDidMount()

componentWillReceiveProps()

shouldComponentUpdate()

componentWillUpdate()

componentDidUpdate()

componentWillUnmount()

```
## задача

Метод componentWillMount() вызывается перед методом render(), когда компонент монтируется в DOM. Зарегистрируйте что-нибудь на консоли в componentWillMount() - вы можете захотеть открыть консоль браузера, чтобы увидеть результат.
* MyComponent should render a div element.
* console.log should be called in componentWillMount.
```
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
  }
  componentWillMount() {
    // change code below this line
    console.log(1222);
    // change code above this line
  }
  render() {
    return <div />
  }
};
```
#  метод жизненного цикла componentDidMount

Большинству веб-разработчиков в какой-то момент необходимо вызвать конечную точку API для получения данных. Если вы работаете с React, важно знать, где выполнить это действие.

Лучше всего с React размещать вызовы API или любые вызовы вашего сервера в методе жизненного цикла componentDidMount(). Этот метод вызывается после монтирования компонента в DOM. Любые вызовы setState () здесь вызовут повторную визуализацию вашего компонента. Когда вы вызываете API в этом методе и устанавливаете свое состояние с данными, которые возвращает API, оно автоматически инициирует обновление, как только вы получите данные.

## задача

В componentDidMount() есть ложный вызов API. Он устанавливает состояние через 2,5 секунды, чтобы имитировать вызов сервера для получения данных. В этом примере запрашивается общее количество активных пользователей сайта. В методе рендеринга выведите значение activeUsers в h1. Посмотрите, что происходит в предварительном просмотре, и не стесняйтесь изменять время ожидания, чтобы увидеть различные эффекты.

```
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      activeUsers: null
    };
  }
  componentDidMount() {
    setTimeout( () => {
      this.setState({
        activeUsers: 1273
      });
    }, 2500);
  }
  render() {
    return (
      <div>
        <h1>Active Users: { /* change code here */ }</h1>
      </div>
    );
  }
};
```
* MyComponent should render a div element which wraps an h1 tag.
* Component state should be updated with a timeout function in componentDidMount.
* The h1 tag should render the activeUsers value from MyComponent's state.

```
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      activeUsers: null
    };
  }
  componentDidMount() {
    setTimeout( () => {
      this.setState({
        activeUsers: 1273
      });
    }, 2500);
  }
  render() {
    return (
      <div>
        <h1>Active Users: { this.state.activeUsers }</h1>
      </div>
    );
  }
};
```