# Доступ к PROPS с помощью this.props

Последние несколько проблем касались основных способов передачи PROPS дочерним компонентам. Но что, если дочерний компонент, которому вы передаете PROPS, является компонентом класса ES6, а не функциональным компонентом без состояния? Компонент класса ES6 использует немного другое соглашение для доступа к PROPS.

Каждый раз, когда вы ссылаетесь на компонент класса внутри себя, вы используете ключевое слово this. Чтобы получить доступ к реквизитам внутри компонента класса, вы должны предварять код, который вы используете для доступа к нему с этим. Например, если компонент класса ES6 имеет реквизит, называемый data, вы пишете {this.props.data} в JSX.

# ЗАДАНИЕ
Визуализируйте экземпляр компонента ReturnTempPassword в родительском компоненте ResetPassword. Здесь дайте ReturnTempPassword PROP tempPassword и присвойте ему значение строки длиной не менее 8 символов. Внутри дочернего элемента ReturnTempPassword перейдите к PROP tempPassword внутри strong tags, чтобы убедиться, что пользователь видит временный пароль.
* The ResetPasswordcomponent should return a single divelement.
* The fourth child of ResetPasswordshould be the ReturnTempPasswordcomponent.
* The ReturnTempPasswordcomponent should have a prop called tempPassword.
* The tempPasswordprop of ReturnTempPasswordshould be equal to a string of at least 8characters.
* The ReturnTempPasswordcomponent should display the password you create as the tempPasswordprop within strongtags.

```
class ReturnTempPassword extends React.Component {
  constructor(props) {
    super(props);

  }
  render() {
    return (
        <div>
            { /* change code below this line */ }
            <p>Your temporary password is: <strong>*5*{this.props.tempPassword}
 </strong></p>
            { /* change code above this line */ }
        </div>
    );
  }
};

class ResetPassword extends React.Component {
  constructor(props) {
    super(props);

  }
  render() {
    return (
        <div>
          <h2>Reset Password</h2>
          <h3>We've generated a new temporary password for you.</h3>
          <h3>Please reset this password from your account settings ASAP.</h3>
          { /* change code below this line */ }
//1 – 4   <ReturnTempPassword tempPassword='12345678'/>

          { /* change code above this line */ }
        </div>
    );
  }
};
```
# Обзор использования PROPS с функциональными компонентами без сохранения состояния

Вы передавали реквизиты функциональным компонентам без сохранения состояния. Эти компоненты действуют как чистые функции. Они принимают реквизиты в качестве входных данных и возвращают одно и то же представление каждый раз, когда им передаются одинаковые реквизиты.
Функциональный компонент без сохранения состояния stateless functional component  - это любая написанная вами функция, которая принимает PROPS и возвращает JSX. Компонент без сохранения состояния, с другой стороны, является классом, который расширяет React.Component, но не использует внутреннее состояние (рассматривается в следующей задаче). 
Распространенным примером является попытка создавать функциональные компоненты без состояния, где это возможно. Это улучшает разработку и обслуживание вашего приложения, упрощая отслеживание того, как изменения состояния влияют на его поведение.

# ЗАДАЧА
Редактор кода имеет компонент CampSite, который отображает компонент Camper как дочерний. Определите компонент Camper и назначьте ему PROPS по умолчанию {name: 'CamperBot'}. Внутри компонента Camper визуализируйте любой код, который вы хотите, но убедитесь, что у вас есть один элемент p, который включает в себя только значение имени, которое передается как PROP. Наконец, определите propTypes в компоненте Camper, чтобы требовать, чтобы имя было указано как prop, и убедитесь, что оно имеет тип string.

* The CampSitecomponent should render.
* The Campercomponent should render.
* The Campercomponent should include default props which assign the string CamperBotto the key name.
* The Campercomponent should include prop types which require the name prop to be of type string.
* The Campercomponent should contain a p element with only the text from the name prop.

```
class CampSite extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <Camper/>
      </div>
    );
  }
};
// change code below this line
const Camper = props => (<p>{props.name}</p>);

Camper.defaultProps = {
  name: 'CamperBot'
};

Camper.propTypes = {
  name: PropTypes.string.isRequired
};
```
