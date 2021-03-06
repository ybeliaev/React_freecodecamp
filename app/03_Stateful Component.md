# Создать компонент с состоянием

Одной из самых важных тем в React является состояние. Состояние состоит из любых данных, о которых должно знать ваше приложение, которые могут со временем меняться.

Вы создаете состояние в компоненте React, объявив свойство state в классе компонента в его конструкторе. Это инициализирует компонент с состоянием, когда он создается. Свойство state должно быть установлено в объект JavaScript. Объявление это выглядит так:

```
this.state = {
  // describe your state here
}
```
У вас есть доступ к объекту state в течение всего срока службы вашего компонента. Вы можете обновить его, отобразить в своем пользовательском интерфейсе и передать в качестве props  дочерним компонентам. Объект state может быть настолько сложным или настолько простым, насколько вам нужно. Обратите внимание, что вы должны создать компонент класса, расширив React.Component, чтобы создать подобное состояние.

## задача

В редакторе кода есть компонент, который пытается отобразить свойство name из его state. Тем не менее, state не определено. Инициализируйте компонент сo state в конструкторе и присвойте свое имя свойству name.

```
class StatefulComponent extends React.Component {
  constructor(props) {
    super(props);
    // initialize state here

  }
  render() {
    return (
      <div>
        <h1>{this.state.name}</h1>
      </div>
    );
  }
};
```

## решение

```
class StatefulComponent extends React.Component {
  constructor(props) {
    super(props);
    // initialize state here
    
    this.state = {
      name : "Name"
    }

  }
  render() {
    return (
      <div>
        <h1>{this.state.name}</h1>
      </div>
    );
  }
};
```

# Render State in the User Interface

Определив начальное state компонента, вы можете отобразить любую его часть в отображаемом пользовательском интерфейсе. Если компонент с состоянием, он всегда будет иметь доступ к данным в state в своем методе render (). Вы можете получить доступ к данным с помощью this.state.

Если вы хотите получить доступ к значению состояния в return методе render , вы должны заключить это значение в фигурные скобки.

State - одна из самых мощных фич компонентов в React. Это позволяет вам отслеживать важные данные в вашем приложении и отображать пользовательский интерфейс в ответ на изменения этих данных. Если ваши данные изменятся, ваш интерфейс изменится. React использует так называемый виртуальный DOM, чтобы отслеживать изменения за кулисами. Когда данные состояния обновляются, он запускает повторную визуализацию компонентов, использующих эти данные, включая дочерние компоненты, которые получили данные в качестве реквизита. React обновляет фактический DOM, но только там, где это необходимо. Это означает, что вам не нужно беспокоиться об изменении DOM. Вы просто объявляете, как должен выглядеть пользовательский интерфейс.

Обратите внимание, что если вы сделаете компонент с состоянием, другие компоненты не будут знать о его state. Его state полностью инкапсулировано или является локальным для этого компонента, если только вы не передаете данные состояния дочернему компоненту в качестве props. Это понятие инкапсулированного state очень важно, потому что оно позволяет вам написать определенную логику, а затем хранить и изолировать эту логику в одном месте вашего кода.

## задача

В редакторе кода MyComponent уже с состоянием. Определите тег h1 в методе render  компонента, который отображает значение name из состояния компонента.

Примечание: h1 должен отображать значение только из state и ничего больше. В JSX любой код, который вы пишете с помощью фигурных скобок {}, будет обрабатываться как JavaScript. Таким образом, чтобы получить доступ к значению из состояния, просто заключите ссылку в фигурные скобки.
* MyComponent should have a key name with value freeCodeCamp stored in its state.
* MyComponent should render an h1 header enclosed in a single div.
* The rendered h1 header should contain text rendered from the component's state.

```
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      name: 'freeCodeCamp'
    }
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
```
## решение

```
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      name: 'freeCodeCamp'
    }
  }
  render() {
    return (
      <div>
        { /* change code below this line */ }
        <h1>{this.state.name}</h1>
        { /* change code above this line */ }
      </div>
    );
  }
};
```