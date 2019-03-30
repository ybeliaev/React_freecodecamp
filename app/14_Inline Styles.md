# Представляем встроенные стили

Если вы импортируете стили из таблицы стилей, они практически не отличаются. Вы применяете класс к своему элементу JSX, используя атрибут className, и применяете стили к классу в своей таблице стилей. Другим вариантом является применение встроенных стилей, которые очень распространены в разработке ReactJS.

Вы применяете встроенные стили к элементам JSX аналогично тому, как вы делаете это в HTML, но с некоторыми отличиями в JSX. Вот пример встроенного стиля в HTML:
```<div style="color: yellow; font-size: 16px">Mellow Yellow</div>```

Элементы JSX используют атрибут style, но из-за способа переноса JSX вы не можете установить значение в string. Вместо этого вы устанавливаете его равным объекту JavaScript. Вот пример:

```<div style={{color: "yellow", fontSize: 16}}>Mellow Yellow</div>```

Заметьте, как мы пришли в свойство «fontSize»? Это связано с тем, что React не будет принимать ключи kebab-case в объекте стиля. React применит правильное имя свойства для нас в HTML.

## задание

Добавьте атрибут стиля в div в редакторе кода, чтобы придать тексту красный цвет и размер шрифта 72 пикселя. 
Обратите внимание, что вы можете при желании установить размер шрифта в виде числа, пропуская единицы «px», или записать его как «72px».
```
class Colorful extends React.Component {
  render() {
    return (
      <div>Big Red</div>
    );
  }
};
```
* The component should render a div element.
* The div element should have a color of red.
* The div element should have a font size of 72px.

```
class Colorful extends React.Component {
  render() {
    return (
      <div style={{ color: 'red', fontSize: '72'}}>
        Big Red
      </div>
    );
  }
};
```
Обратите внимание, что атрибут JSX - camelCase. Это еще одно важное отличие, которое следует помнить о JSX. Кроме того, вы, вероятно, заметили, что нет px. В JSX, при установке атрибута fontSize, px является необязательным и будет автоматически установлен , если он не установлен вручную.

# Add Inline Styles

Вы, возможно, заметили в последней задаче, что было несколько других отличий синтаксиса от встроенных стилей HTML в дополнение к атрибуту style, установленному для объекта JavaScript. Во-первых, имена определенных свойств стиля CSS используют верблюжий регистр. Например, последняя задача - установить размер шрифта с помощью fontSize вместо font-size. Дефисные слова, такие как font-size, являются недопустимым синтаксисом для свойств объекта JavaScript, поэтому React использует camel case. Как правило, любые свойства стиля через дефис пишутся с использованием camel case в JSX.

Все единицы длины значения свойства (например, высота, ширина и fontSize) переводятся в пиксели, если не указано иное. Например, если вы хотите использовать em, вы заключаете значение и единицы в кавычки, например {fontSize: "4em"}. Кроме значений длины, которые по умолчанию равны px, все остальные значения свойств должны быть заключены в кавычки.

## задача

Если у вас большой набор стилей, вы можете назначить объект стиля константе, чтобы сохранить ваш код организованным. Раскомментируйте константу стилей и объявите объект с тремя свойствами стиля и их значениями. Дайте div цвет «фиолетовый», размер шрифта 40 и границу «2px solid purple». Затем установите атрибут стиля равным константе стилей.

```
// const styles =
// change code above this line
class Colorful extends React.Component {
  render() {
    // change code below this line
    return (
      <div style={{color: "yellow", fontSize: 24}}>Style Me!</div>
    );
    // change code above this line
  }
};
```
* The styles variable should be an object with three properties.
* The styles variable should have a color property set to a value of purple.
* The styles variable should have a fontSize property set to a value of 40.
* The styles variable should have a border property set to a value of 2px solid purple.
* The component should render a div element.
* The div element should have its styles defined by the styles object.

```
const styles = {color: "purple", fontSize: 40, border: "2px solid purple"}
// change code above this line
class Colorful extends React.Component {
  render() {
    // change code below this line
    return (
      <div style={styles}>Style Me!</div>
    );
    // change code above this line
  }
};
```