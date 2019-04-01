# Use Array.filter() to Dynamically Filter an Array

Метод массива map - это мощный инструмент, который вы будете часто использовать при работе с React. Другим методом, связанным с map, является filter, который фильтрует содержимое массива на основе условия, а затем возвращает новый массив. Например, если у вас есть массив пользователей, у каждого из которых есть свойство онлайн, которое может быть установлено в true или false, вы можете отфильтровать только тех пользователей, которые находятся в сети, написав:
```let onlineUsers = users.filter(user => user.online);```

## task

В редакторе кода state MyComponent инициализируется массивом пользователей. Некоторые пользователи онлайн, а некоторые нет. Фильтруйте массив так, чтобы вы видели только пользователей, которые в сети. Для этого сначала используйте filter, чтобы вернуть новый массив, содержащий только пользователей, чье online-свойство имеет значение true. Затем в переменной renderOnline отобразите отфильтрованный массив и верните элемент li для каждого пользователя, который содержит текст его имени пользователя. Не забудьте также включить уникальный ключ, как в последних задачах.

* MyComponent should exist and render to the page.
* MyComponent's state should be initialized to an array of six users.")
* MyComponent should return a div, an h1, and then an unordered list containing li elements for every user whose online status is set to true.
* MyComponent should render li elements that contain the username of each online user.
* Each list item element should have a unique key attribute.
```
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      users: [
        {
          username: 'Jeff',
          online: true
        },
        {
          username: 'Alan',
          online: false
        },
        {
          username: 'Mary',
          online: true
        },
        {
          username: 'Jim',
          online: false
        },
        {
          username: 'Sara',
          online: true
        },
        {
          username: 'Laura',
          online: true
        }
      ]
    }
  }
  render() {
    const usersOnline = null; // change code here
    const renderOnline = null; // change code here
    return (
       <div>
         <h1>Current Online Users:</h1>
         <ul>
           {renderOnline}
         </ul>
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
      users: [
        {
          username: 'Jeff',
          online: true
        },
        {
          username: 'Alan',
          online: false
        },
        {
          username: 'Mary',
          online: true
        },
        {
          username: 'Jim',
          online: false
        },
        {
          username: 'Sara',
          online: true
        },
        {
          username: 'Laura',
          online: true
        }
      ]
    }
  }
  render() {
    const usersOnline = this.state.users.filter(i => i.online == true); 
    const renderOnline = usersOnline.map((i) => <li key={i.username + 1}>{i.username}</li>);
    return (
       <div>
         <h1>Current Online Users:</h1>
         <ul>
           {renderOnline}
         </ul>
       </div>
    );
  }
};
```
