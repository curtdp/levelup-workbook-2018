# Таблицы

**Jon Dukket HTML & CSS Глава 6 стр. 126**

[Примеры кода](http://www.htmlandcssbook.com/code-samples/chapter-06/)

## Элементы

- [`<table>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/table) — используется для создания таблицы, данные представлены построчно.
- [`<tr>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/tr) — table row, строка таблицы, внутри которой следуют несколько ячеек таблицы
- [`<td>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/td) — table data, ячейка таблицы, содержит собственно данные таблицы.
- [`<th>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/th) — table heading, используется как `<td>`, но содержит заголовок колонки или строки таблицы. Семантический элемент который помогает скринридерам и поисковым системам правильно интерпретировать данные таблицы.

Даже если ячейка не содержит данных, её нужно всё равно использовать в таблице, иначе таблица может отображаться не корректно.

### Атрибут scope для `<th>`

Используется для указания к чему относится заголовок таблицы, к колонке или строке. **Считается устаревшим в HTML5,** [но на него всё ещё опираются некоторые скринридеры](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/table#Scoping_rows_and_columns).

```html
<th scope="row">

<th scope="column">
```

Соответствует стандартам использование атрибута [`headers`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/td#attr-headers) на `<td>` и `<th>`

[https://webref.ru/layout/html5-css3/table](https://webref.ru/layout/html5-css3/table)

###  Атрибуты:

`colspan` — для объединения ячеек по горизонтали

`rowspan` — для объединения ячеек по вертикали

### Задание

[https://htmlacademy.ru/courses/39/run/14](https://htmlacademy.ru/courses/39/run/14)

![](/articles/2018.09.16/DraggedImage.jpeg)

Атрибут `colspan`

### Задание

[https://htmlacademy.ru/courses/39/run/15](https://htmlacademy.ru/courses/39/run/15)

![](/articles/2018.09.16/DraggedImage-1.jpeg)

Атрибут `rowspan`

### [Продвинутые таблицы](https://developer.mozilla.org/ru/docs/Learn/HTML/Tables/Advanced)

- [`<caption>`](https://developer.mozilla.org/ru/docs/Web/HTML/Element/caption)
- [`<col>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/col)
- [`<colgroup>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/colgroup)
- [`<thead>`](https://developer.mozilla.org/ru/docs/Web/HTML/Element/thead)
- [`<tfoot>`](https://developer.mozilla.org/ru/docs/Web/HTML/Element/tfoot)
- [`<tbody>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/tbody)

### Стили таблиц

Повтор шапки и подвала при печати

[https://codepen.io/curtdp/pen/LJJjOV](https://codepen.io/curtdp/pen/LJJjOV)

## Полный Гайд по таблицам

[https://css-tricks.com/complete-guide-table-element/](https://css-tricks.com/complete-guide-table-element/)

## Таблицы на HTMLAcademy

[Знакомство с таблицами](https://htmlacademy.ru/courses/39)


# Формы

В этом разделе основной материал по отсылкам в книги

**Jon Dukket HTML & CSS Глава 7 стр. 145**

[Примеры кода](http://www.htmlandcssbook.com/code-samples/chapter-07/)

[https://webref.ru/course/html-content/forms](https://webref.ru/course/html-content/forms)

## Отправка данных

### Запросы

HTML формы могут совершать только два вида http запросов:

- [GET](https://ru.wikipedia.org/wiki/HTTP#GET)
- [POST](https://ru.wikipedia.org/wiki/HTTP#POST)

Тип запроса указывается в атрибуте `method`, если атрибут не указан, по-умолчанию используется метод GET.

### [`<input type="hidden">`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/hidden)
Скрытое поле
- токен для защиты от [csrf](https://ru.wikipedia.org/wiki/%D0%9C%D0%B5%D0%B6%D1%81%D0%B0%D0%B9%D1%82%D0%BE%D0%B2%D0%B0%D1%8F_%D0%BF%D0%BE%D0%B4%D0%B4%D0%B5%D0%BB%D0%BA%D0%B0_%D0%B7%D0%B0%D0%BF%D1%80%D0%BE%D1%81%D0%B0)
- метаданные к запросу (id записи откуда отправлены данные (комментарий, редактирование записи) и т. п.)

## HTML5 формы

**Кит Джереми HTML5 для веб-дизайнеров, глава 4. Веб-формы 2.0**