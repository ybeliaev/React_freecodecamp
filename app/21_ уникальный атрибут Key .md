# Присвойте дочерним элементам уникальный  атрибут Key 

Последняя задача показала, как метод map используется для динамического рендеринга ряда элементов на основе пользовательского ввода. Тем не менее, в этом примере отсутствовала важная часть. Когда вы создаете массив элементов, каждому из них необходим ключевой атрибут с уникальным значением. React использует эти ключи для отслеживания того, какие элементы добавлены, изменены или удалены. Это помогает сделать процесс повторного рендеринга более эффективным, когда список каким-либо образом изменяется. Обратите внимание, что ключи должны быть уникальными только между одноуровневыми элементами, они не обязательно должны быть глобально уникальными в вашем приложении.

## task

Редактор кода имеет массив с некоторыми внешними средами и функциональным компонентом без сохранения состояния с именем Frameworks(). Frameworks() должен сопоставить массив с неупорядоченным списком, как в последнем вызове. Завершите написание обратного вызова карты, чтобы вернуть элемент li для каждого фреймворка в массиве frontEndFrameworks. На этот раз убедитесь, что каждому li присвоен ключевой атрибут с уникальным значением.
Обычно вы хотите сделать ключ чем-то, что однозначно идентифицирует отображаемый элемент. В качестве последнего средства можно использовать индекс массива, но обычно вы должны попытаться использовать уникальную идентификацию.
```
const frontEndFrameworks = [
  'React',
  'Angular',
  'Ember',
  'Knockout',
  'Backbone',
  'Vue'
];

function Frameworks() {
  const renderFrameworks = null; // change code here
  return (
    <div>
      <h1>Popular Front End JavaScript Frameworks</h1>
      <ul>
        {renderFrameworks}
      </ul>
    </div>
  );
};
```
* The Frameworks component should exist and render to the page.
* Frameworks should render an h1 element.
* Frameworks should render a ul element.
* The ul tag should render 6 child li elements.
* Each list item element should have a unique key attribute.

```
const frontEndFrameworks = [
  'React',
  'Angular',
  'Ember',
  'Knockout',
  'Backbone',
  'Vue'
];

function Frameworks() {
  const renderFrameworks = frontEndFrameworks.map((item) =>
  <li key={item+1}>{item}</li>
);
  return (
    <div>
      <h1>Popular Front End JavaScript Frameworks</h1>
      <ul>
        {renderFrameworks}
      </ul>
    </div>
  );
};
```