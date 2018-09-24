# CSS — Cascading Style Sheets

[CSS](https://developer.mozilla.org/ru/docs/Web/CSS) позволяет создавать правила которые указывают как должно выглядеть содержимое элемента.

Когда мы научимся **как** писать правила CSS, дальнейшее изучение CSS будет состоять, по большей части, из изучения различных свойств.

[Wikipedia про CSS](https://ru.wikipedia.org/wiki/CSS)

## Введение

> Cascading Style Sheets (CSS) — это язык иерархических правил (таблиц стилей), используемый для представления внешнего вида документа, написанного на HTML или XML (включая различные языки XML, такие как SVG и XHTML). CSS описывает, каким образом элемент должен отображаться на экране, на бумаге, голосом или с использованием других медиа средств.
>
> CSS используется для стилизации и верстки веб-страниц. С помощью него можно менять шрифты, цвета, расстояние между блоками, разделять контент на колонки, добавлять анимацию и прочие декоративные элементы.

[https://developer.mozilla.org/ru/docs/Web/CSS](https://developer.mozilla.org/ru/docs/Web/CSS)
[Как работает CSS](https://developer.mozilla.org/ru/docs/Learn/CSS/Introduction_to_CSS/How_CSS_works)

  CSS влияет на DOM, а не на сам HTML.

## Литература и инструменты для раздела

### Эрик А. Мейер — CSS. Каскадные таблицы стилей. Подробное руководство

Читать c начала и до главы 3 «структура и каскад» включительно.

![Разница между изданиями 2 редакция 576 страниц и 4 издание более 1000 страниц](/articles/2018.09.19/DraggedImage.jpeg "CSS The Definitive Guide 4th vs 2nd edition")

Разница между изданиями — 13 лет

[Примеры кода](https://meyerweb.github.io/csstdg4figs/index.html) — Github pages
[Примеры кода](https://github.com/meyerweb/csstdg4figs) — репозиторий git

### Jon Dukket

Читаем главу 10. И помним что материал немного устарел, например атрибут `type` для элемента `<link>` можно не указывать при подключении CSS.

### Сайт с примерами стилизации одного документа, разными стилями

[http://www.csszengarden.com](http://www.csszengarden.com) — один документ, но разные стили.

Изучаем с инспектором браузера.

## Как CSS влияет на HTML?

Браузер применяет CSS правила к документу, чтобы описать, как он будет отображаться. CSS-правила формируются из:

- Набора свойств, которые имеют значения, устанавливающие, как будет отображаться содержимое (HTML), Например Я хочу, чтобы ширина элемента равнялась 50% ширины родительского элемента, и его фон был красным.
- Селектор, который выбирает (англ. selects)  элемент/элементы, к которым вы хотите применить измененные значения. Например, Я хочу применить это CSS-правило ко всем параграфам в моем HTML-документе.

[Синтаксис](https://developer.mozilla.org/ru/docs/Web/CSS/%D0%A1%D0%B8%D0%BD%D1%82%D0%B0%D0%BA%D1%81%D0%B8%D1%81)

### Пример правила

```css
p {
  font-family: Arial;
  color: #666666;
}
```

### Инструменты

- Инструменты разработчика Chrome & Firefox Inspectors — вкладка styles
- Плагин для Chrome [Pecticide](https://chrome.google.com/webstore/detail/pesticide-for-chrome/bblbgcheenepgnnajgfpiicnbbdmmooh) — показывает контуры элементов страницы, выделенные рамками разного цвета
- Web Developer — плагин для [Chrome](https://chrome.google.com/webstore/detail/web-developer/bfbameneiokkgbdmiekhjnmfkcnldhhm?hl=ru) и для [Firefox](https://addons.mozilla.org/ru/firefox/addon/web-developer/)
- [CSS Валидатор w3c](http://jigsaw.w3.org/css-validator/)

## Кроссбраузерная совместимость

[Почему бывают кроссбраузерные проблемы](https://developer.mozilla.org/en-US/docs/Learn/Tools_and_testing/Cross_browser_testing/Introduction)

- Баги браузеров, различная реализация одних и тех же функций. (Раньше компании делали разные реализации сознательно, стремясь получить конкурентное преимущество, создавая проблемы разработчикам)
- Некоторые браузеры имеют разный уровень реализации технической функциональности (особенно новейшей, до стандартизации)
- некоторые устройства имеют ограничения, которые приводят к тому, что сайт работает медленно или плохо отображается.

## Подключение стилей

Способы подключения стилей к документу.

### из внешнего css-файла элементом link

```html
<link rel="stylesheet" type="text/css" href="style.css">
```

В современном варианте можно не указывать атрибут `type`

```html
<link rel="stylesheet" href="style.css">
```

### В теге [`<style>`](https://www.w3.org/TR/html52/document-metadata.html#the-style-element) (по старым правилам только внутри head), а с HTML 5.2 можно и в `<body>`

```html
<style>
  p {
    font-size: 18px;
    color: blue;
  }

  .highlight {
    background-color: yellow;
  }
</style>
```

### Правило @import

```html
<style>
  @import "style.css";
</style>
```

[Проблема import](http://stevesouders.com/tests/atimport/link-with-import.php?t=1509131756) — блокировка загрузки

### inline css в атрибуте `style` элемента

```html
<p style="font-size: 20px; color: blue;">Текст параграфа с <mark style="background-color:burlywood;">выделенным</mark> фрагментом.</p>
```

## Стили по умолчанию

У разных браузеров могут быть различные стили по умолчанию
[https://stackoverflow.com/questions/6867254/browsers-default-css-for-html-elements](https://stackoverflow.com/questions/6867254/browsers-default-css-for-html-elements)

### Подходы к приведению к общему виду

- [reset.css](https://meyerweb.com/eric/tools/css/reset/)
- [normalize.css](https://github.com/necolas/normalize.css)
- [CSS Box Model](https://www.smashingmagazine.com/2010/06/the-principles-of-cross-browser-css-coding/#understand-the-css-box-model)

## Идентификаторы и классы

Атрибуты для выборки элементов

### Id

- `id` — идентификатор элемента, должен быть уникален для всего документа. `id="uniqueName"`

### Class

`class` — класс документа, используется чтобы выделить группу элементов со схожим смыслом, для использования в css или javascript.

Значением атрибута `class` может быть несколько слов, могут быть повторы:

```html
<p class="warning message">Первый</p>
<p class="info message">Второй</p>
<p class="error message">Третий</p>
```

```html
<p id="welcome">Приветственный текст</p>

<p class="faq is-active">Какой-то другой текст</p>
```

## Селекторы

[https://webref.ru/course/css-tutorial/selector](https://webref.ru/course/css-tutorial/selector)

- `p` - селектор элемента
- `.className` - селектор класса
- `#idName` - селектор идентификатора
- `*` - универсальный селектор
- `h1, h2, .className, #idName` - группировка селекторов
- `h1 .className` - вложенный элемент
- `[id="idName"]` - селектор атрибута
- `[data-url="http://url"]` — селектор атрибута с значением
- `.message.warning` - селектор множественного класса (так же можно комбинировать селекторы элемента и атрибута)

Селекторы классов и идентификаторов позволяют присваивать стили к элементам вне зависимости от структуры документа (в отличие от селекторов элементов).

- [Простые селекторы](https://developer.mozilla.org/ru/docs/Learn/CSS/Introduction_to_CSS/Simple_selectors) (Simple selectors): Указывают на один или несколько элементов на основании типа элемента, класса (class), или id элемента.
- [Селекторы атрибутов](https://developer.mozilla.org/ru/docs/Learn/CSS/Introduction_to_CSS/Attribute_selectors) (Attribute selectors): Указывают на один или несколько элементов на основании их атрибутов/значений атрибутов.
- [Псевдоклассы](https://developer.mozilla.org/ru/docs/Learn/CSS/Introduction_to_CSS/Pseudo-classes_and_pseudo-elements#%D0%9F%D1%81%D0%B5%D0%B2%D0%B4%D0%BE%D0%BA%D0%BB%D0%B0%D1%81%D1%81%D1%8B) (Pseudo-classes): Указывают на один или несколько элементов, находящихся в определенном состоянии, например те на которые наведен курсор мыши, выделенные или неактивные элементы, или, скажем, элемент, являющийся первым потомком своего родителя в дереве DOM.
- [Псевдоэлементы](https://developer.mozilla.org/ru/docs/Learn/CSS/Introduction_to_CSS/Pseudo-classes_and_pseudo-elements#%D0%9F%D1%81%D0%B5%D0%B2%D0%B4%D0%BE%D1%8D%D0%BB%D0%B5%D0%BC%D0%B5%D0%BD%D1%82%D1%8B) (Pseudo-elements): Указывают одну или несколько частей содержимого страницы, определенным образом расположенные по отношению к элементу: например, первое слово в каждом параграфе или что-либо прямо перед элементом.
- [Комбинаторы](https://developer.mozilla.org/ru/docs/Learn/CSS/Introduction_to_CSS/Combinators_and_multiple_selectors) (Combinators): Это не селекторы как таковые, а способы объединения селекторов для выбора по нескольким условиям одновременно. Например, можно выбрать только те параграфы, которые являются прямыми потомками элементов div или которые следуют сразу за заголовком.
- [Группы селекторов](https://developer.mozilla.org/ru/docs/Learn/CSS/Introduction_to_CSS/Combinators_and_multiple_selectors#%D0%9D%D0%B5%D1%81%D0%BA%D0%BE%D0%BB%D1%8C%D0%BA%D0%BE_%D1%81%D0%B5%D0%BB%D0%B5%D0%BA%D1%82%D0%BE%D1%80%D0%BE%D0%B2_%D0%B2_%D0%BE%D0%B4%D0%BD%D0%BE%D0%BC_%D0%BF%D1%80%D0%B0%D0%B2%D0%B8%D0%BB%D0%B5) (Multiple selectors): Идея здесь в том, что в одном CSS-правиле можно разместить несколько селекторов, отделив их друг от друга запятыми - тогда соответсвующий набор объявлений применяется сразу ко всем элементам, на которые указывают эти селекторы.

[Список всех вариантов селекторов](https://www.w3.org/TR/2018/PR-selectors-3-20180911/#selectors) (спецификация)

## Упражнения

### HTML Academy

- [Глава 1: Знакомство с CSS](https://htmlacademy.ru/courses/41) — пробуйте наперед, если чувствуете что не можете разобраться самостоятельно, оставляйте. На занятиях разберем все детально.
