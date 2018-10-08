# Контексты форматирования в CSS

Спецификация CSS определяет термин **контекст форматирования** как-то так:

> …окружение в котором располагается набор связанных боксов. Различные контексты форматирования располагают свои боксы в соответствии с разными правилами. Например, контекст форматирования flex располагает свои боксы в соответствии с правилами CSS3-FLEXBOX, в то время как контекст форматирования блока располагает боксы в соответствии с блочными и строчными правилами расположения CSS2.

([https://drafts.csswg.org/css-display-3/#formatting-context](https://drafts.csswg.org/css-display-3/#formatting-context))

Мы начнем с рассмотрения уже известного контекста форматирования блоков Block Formatting Context (BFC).

## Блочный контекст форматирования

Создание нового BFC на элементе позволяет создавать независимое окружение расположения для потомков этого элемента.

Новый BFC создается всякий раз когда элемент:

- Является корневым элементом
- Плавающий (floated)
- Имеет `position: absolute` или
- Имеет `display: inline-block`.

Новый BFC также создается если свойство `overflow` имеет значение отличное от `visible`. Флекс элементы, Грид элементы, ячейки таблиц также устанавливают новый контекст форматирования блока для своих элементов-потомков.

[https://codepen.io/curtdp/pen/wYGOVP?editors=1100](https://codepen.io/curtdp/pen/wYGOVP?editors=1100)

У границ различных контекстов форматирования поля не схлопываются.

[https://codepen.io/curtdp/pen/NOrxmo?editors=1100](https://codepen.io/curtdp/pen/NOrxmo?editors=1100)

[https://drafts.csswg.org/css-display-3/#formatting-context](https://drafts.csswg.org/css-display-3/#formatting-context)

## Выпадение из потока

Плавающий элемент или элемент спозиционированный абсолютно — выпадает из потока.

Заметка: Некоторые контексты форматирования подавляют floating, тогда такие элементы не выпадают из потока. `flex` `grid`

## Автоматическая «блокификация»

[https://drafts.csswg.org/css-display-3/#blockify](https://drafts.csswg.org/css-display-3/#blockify)

### Примеры

Некоторые примеры исправления `display`:

- Абсолютно спозиционированный или floated элемент становится `block`
- Родитель с `display: grid | flex` делает элемент блочным

## В потоке и вне потока

Когда мы делали float элемент внутри контейнера, я объяснял, что контейнер схлопнулся потому что плавающий элемент выпал из потока. Элементы которые находятся в потоке, отображаются в соответствии с их моделью форматирования. Модель форматирования блочных элементов означает, что они занимают всю ширину контейнера и добавляют переносы строк перед и после элемента (появляются с новой строки). Строчные элементы отображаются на одной строке если им хватает места — как слова в предложении.

Элемент выпадает из потока, если мы установим ему `position: absolute` или `position: fixed`. Для плавающих элементов это значит, что элемент будет подниматься вверх пока не встретит блочный элемент. Последующие элементы будут обтекать его по краям.

Обратите внимание, только лайнбоксы строчных элементов обтекают плавающие элементы, блоки попадают под плавающий элемент.

## Floats

Как располагать блоки, чтобы они были связаны между собой по плану.

```html
<style>
  .box-1 {
    border: 1px solid black;
    color: white;
    background-color: blue;
    height: 150px;
    width: 300px;
  }
  .box-2 {
    border: 1px solid black;
    color: white;
    background-color: red;
    height: 100px;
    width: 300px;
  }
  .box-3 {
    border: 1px solid black;
    color: white;
    background-color: green;
    height: 200px;
    width: 100px;
  }
</style>
<div class="box-1">1</div>
<div class="box-2">2</div>
<div class="box-3">3</div>
```

Float используется, если нельзя использовать `flex`,

```html
<style>
  .floated div {
    float: left;
  }
</style>
<div class="floated">
  <div class="box-1">1</div>
  <div class="box-2">2</div>
  <div class="box-3">3</div>
</div>
```

### Clearfix

[https://css-tricks.com/snippets/css/clear-fix/](https://css-tricks.com/snippets/css/clear-fix/)

```css
.clearfix::after {
  content: "";
  display: table;
  clear: both;
}
```

#### Пример clearfix

[https://www.w3schools.com/howto/howto\_css\_clearfix.asp](https://www.w3schools.com/howto/howto_css_clearfix.asp)

### То для чего придумывался float

Обтекание блоков текстом

[https://csslayoutbookcodesamples.netlify.com/chapter3/float-list.html](https://csslayoutbookcodesamples.netlify.com/chapter3/float-list.html)

Обтекание по кривой

[https://csslayoutbookcodesamples.netlify.com/chapter3/float-shapes.html](https://csslayoutbookcodesamples.netlify.com/chapter3/float-shapes.html)

### Вопрос

Почему первый параграф не выравнивается с `.block1` и как это исправить?

[https://htmlacademy.ru/courses/65/run/8](https://htmlacademy.ru/courses/65/run/8)

![Почему отступ?](%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%202018-10-07%20%D0%B2%2012.17.15.png)

## Позиционирование элементов

### Свойство `position`

[MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/position)

[PEN](https://codepen.io/curtdp/pen/NwaWGv)

#### Static

Если не применять к элементу свойство `position`, его значением по-умолчанию будет `static`. Элементы со значением static появляются в потоке в порядке, определенным документом. Нам нужно назначать static только в том случае, если нам нужно сбросить свойство position.

#### Relative

Добавление `position: relative` к элементу не дает очевидных немедленных изменений. Но когда мы добавим к элементу какие-то из свойств смещения (offset properties) `top`, `right`, `bottom`, `left`, тогда окажется, что мы можем сдвигать элемент относительно его первоначального положения. Это имеет ограниченное применение. Но, position: relative позволяет создать новый блок-контейнер, с новым контекстом. Это может оказаться полезным, когда мы посмотрим на следующее значение свойства `position`, `position: absolute;`

#### Absolute

Абсолютно позиционированный элемент выпадает из потока от края элемента-контейнера используя свойства смещения. В примере имеется контейнер с блоком внутри него. Внутренний блок имеет `position: absolute;`.

[https://csslayoutbookcodesamples.netlify.com/chapter3/position-absolute.html](https://csslayoutbookcodesamples.netlify.com/chapter3/position-absolute.html)

Блок-контейнер в этом примере это вьюпорт, так как больше нет других элементов содержащих этот элемент. В этом примере этот элемент перекрывает меню!

Если мы хотим чтобы блок был спозиционирован внутри `.container` и смещался относительно краев этого контейнера, нам нужно создать новый блочный контекст форматирования. Мы сделаем это, добавив `position: relative;` к `.container`. Также на контейнере установлена высота, если ее убрать, то контейнер схлопнется, не учитывая высоту элемента внутри него. Так происходит потому `.box` выпадает из потока, так что он не участвует в формировании макета родительского элемента.

[PEN](https://codepen.io/curtdp/pen/GYqGLa)

##### Пример с контейнером

Если контейнеру сделать position: relative, а потомкам меньшей высоты чем контент, сделать position: absolute, то этим потомкам можно будет сделать `height: 100%;` и они растянутся

[https://alistapart.com/d/392/content-out-layout/demos/blog-golden.html](https://alistapart.com/d/392/content-out-layout/demos/blog-golden.html)

```css
body {
  font-family: "Lucida Sans", "Lucida Grande", "Lucida Sans Unicode", sans-serif;
  font-size: 16px;
  line-height: 1.4;
  color: #333333;
  overflow-x: hidden;
  padding: 0;
  position: relative;
  background-color: #F0C800;
}

@media only screen and (min-width: 1024px)
  blog-golden.css:229#main-sidebar {
    position: absolute;
    height: 100%;
}
```

#### Fixed

Когда мы абсолютно позиционируем элемент, он появляется там, где мы его спозиционировали в момент загрузки страницы. При прокрутке документа, этот элемент будет также будет прокурчиваться с его содержимым. Фиксированое позиционирование заставляет элемент принять фиксированное место на экране в момент загрузки документа и оставаться на своем месте, не прокручиваясь с остальным контентом.

Элемент с фиксированным позиционированием также использует свойства смещения, они позиционируют элемент относительно вьюпорта. В следующем примере фиксированный элемент находится в 100 пикселях от верха и в 60 пикселях от правого края вьюпорта.

[https://csslayoutbookcodesamples.netlify.com/chapter3/position-fixed.html](https://csslayoutbookcodesamples.netlify.com/chapter3/position-fixed.html)

Обычный пример фиксированного позиционирования — меню, когда прокручиваем длинный документ.

Обратите внимание, что блок выпал из потока и по этому будет перекрывать контента, как в примере, если вьюпорт станет уже — исчезнет место в боковом поле для фиксированного элемента. Если вы не хотите чтобы элемент перекрывал контент, нужно сделать так, чтобы для этого элемента всегда было место. Это обычное дело для элементов с фиксированным или абсолютным позиционированием, когда элемент выпадает из потока, нужен план как поступить с нежелательными перекрытиями контента.

#### Sticky

Более новое значение position, ведёт себя как гибрид static и fixed. Мы уже знаем, что static это начальное значение position для всех элементов. Также мы видели как элементы с фиксированным позиционированием остаются на месте относительно вьюпорта при прокрутке. Элемент со значением sticky ведет себя, как static, до тех пор, пока документ прокручивается до какого-то момента, в который элемент поведет себя как фиксированный.

[https://csslayoutbookcodesamples.netlify.com/chapter3/position-sticky.html](https://csslayoutbookcodesamples.netlify.com/chapter3/position-sticky.html)

В примере, элемент ведет себя как статический, пока его верхний край не достигнет при прокрутке 20 пикселей от верхнего края вьюпорта. В этот момент он «прилипнет» и будет вести себя как элемент с фиксированным позиционированием.

Как более новый метод позиционирования, он имеет меньшую поддержку баузерами, чем другие значения и работает сейчас только в Firefox и Chrome (Safari с префиксами [https://caniuse.com/#feat=css-sticky](https://caniuse.com/#feat=css-sticky)).

Но для такого эффекта можно довольно легко найти [полифил](https://ru.wikipedia.org/wiki/%D0%9F%D0%BE%D0%BB%D0%B8%D1%84%D0%B8%D0%BB)  — [https://github.com/wilddeer/stickyfill](https://github.com/wilddeer/stickyfill).

[https://meyerweb.github.io/csstdg4figs/11-positioning/stickypos.html](https://meyerweb.github.io/csstdg4figs/11-positioning/stickypos.html) смотреть в firefox, chrome

### Читать

- Эрик Мейер глава 10  стр. 344
- Девид Макфарланд Глава 14 с. 462

## Многоколоночные макеты

(MULTIPLE-COLUMN LAYOUT)

Это метод разделения контента на колонки, почти как в газетной верстке. На первый взгляд может показаться, что в вебе это не применимо, но есть хорошие примеры использования.

[https://csslayoutbookcodesamples.netlify.com/chapter3/multicolumn-layout.html](https://csslayoutbookcodesamples.netlify.com/chapter3/multicolumn-layout.html)

Эта спецификация — единственный метод который влияет на куски непрерывного контента и распределяет его по колонкам. Другие методы влияют на элементы-потомки, а не на поток контента (вне зависимости из чего он состоит).

[https://www.w3schools.com/css/css3_multiple_columns.asp](https://www.w3schools.com/css/css3_multiple_columns.asp)

Хороший пример для использования этой спецификации — создание более компактного представления элементов интерфейса, таких как набор чекбоксов. Задавая им `column-width` можно «сокращать» длинную простыню контента во что-то более компактное. Использование column-width значит что элементы могут отображаться в две, три или более колонок, в зависимости от доступного пространства, без необходимости использовать медиа-запросы.

[https://codepen.io/curtdp/pen/zPExOx](https://codepen.io/curtdp/pen/zPExOx)

### Свойства

- `column-width: <length> | auto` — ширина колонки
- `column-count` — количество колонок
- `columns` — устанавливает  `column-width ` и `column-count`
- `column-rule-color` — цвет границы
- `column-rule-style` — стиль границы
- `column-rule-width` — толщина границы
- `column-rule` — короткая запись
- `column-span: none | all;` — объединение колонок, например, для заголовка
- `column-fill: auto | balance | balance-all` — как балансирует контент когда разбивается на колонки.
- `column-gap` — расстояние между колонками

## Flexbox

[https://css-tricks.com/snippets/css/a-guide-to-flexbox/](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)

[Исходные файлы](https://github.com/wesbos/What-The-Flexbox) — [Бесплатный курс (Англ.)](https://flexbox.io)

### Введение

### Направление flexbox

Оси flexbox

Терминология [Spec](https://www.w3.org/TR/css-flexbox-1/#box-model)

- Основная ось
- Поперечная ось

`flex-direction: row | column | row-reverse | column-reverse;`

### Перенос элементов

Когда заканчивается место в контейнере, делается перенос.

`flex-wrap: nowrap | wrap | wrap-reverse`

`wrap-reverse` делает перенос в противоположную сторону от поперечной оси.

### Изменение порядка

[Order](https://developer.mozilla.org/ru/docs/Web/CSS/order)

`order: <integer>` — как бы добавляет вес элементу

Помогает в респонсив дизайне изменять расположение элементов.

Нужно учитывать семантику элементов. Сильно ли поменяется смысл документа если порядок элементов будет изменен.

### Выравнивание и центровка

#### justify-content

[justify-content](https://developer.mozilla.org/ru/docs/Web/CSS/justify-content)

`justify-content` определяет, как браузер распределяет пространство между и вокруг элементов контента вдоль главной оси их контейнера.

`space-between` – на floats такое делать сложнее
`space-around`
`space-evenly`
`center`

Изменяя `flex-direction: column`, уменьшить шрифт чтобы появилось свободное место.

#### align-items

`align-items` распределяет свободное место вдоль поперечной оси контейнера

Добавить высоты контейнеру

`baseline` — сделать разный размер шрифтам элементов

#### align-content

Принимает те же значения что и `justify-content`

Выравнивает строки Флекс-контейнера.

Работает если есть перенос контента, например`flex-wrap: wrap;`

Чтобы элементы начали переноситься нужно как-то увеличить их ширину, например `width: 33.3333%`

Выравнивание элементов вдоль поперечной оси, применяется на контейнере.

#### align-self

Выравнивание элемента вдоль поперечной оси, применяется на индивидуальных Флекс элементах

### Свойство flex

Применяется к элементам, а не к контейнеру.

Определяет как будет расти или уменьшаться элемент, и что брать за основу за ширину элемента. Что делать когда места в контейнере достаточно и что делать если места не хватает.

`flex-grow` — сколько брать места когда распределяется излишнее свободное пространство. По умолчанию 0
`flex-shrink` — как уменьшаться, если свободного места не хватает. По умолчанию 1
`flex-basis` — ширина которая берется за основу, если значение `auto`, тогда берется значение свойства `width`, если и оно не установлено берется ширина контента элемента.

Значения `flex-grow` и `flex-shrink` указываются в пропорциях, просто вещественное число, не пиксели, не проценты.

Для короткой записи `flex` рекомендуется указывать все значения отдельно, не сокращать.
`flex: 1 1 auto`

### Как работает flex-basis с переносом wrap

`flex` работает только в пределах одной строки. Для новой строки расчет, как расти и уменьшаться, будет сделан отдельно. Каждая строка Флекс контейнера является как бы отдельным контейнером.

### Игра-тест

[https://flexboxfroggy.com/#ru](https://flexboxfroggy.com/#ru)

### Читать туториал

[https://medium.freecodecamp.org/the-complete-illustrated-flexbox-tutorial-d35c085dbf35](https://medium.freecodecamp.org/the-complete-illustrated-flexbox-tutorial-d35c085dbf35)