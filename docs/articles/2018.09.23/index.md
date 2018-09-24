# Специфичность (вес селекторов)

Читать: **Эрик Мейер Глава 3**

- [https://developer.mozilla.org/ru/docs/Web/CSS/Specificity](https://developer.mozilla.org/ru/docs/Web/CSS/Specificity)
- [https://webref.ru/course/css-basics/priority](https://webref.ru/course/css-basics/priority)
- [Калькулятор специфичности](https://specificity.keegan.st/)

## Пример расчета специфичности

```text
Пример рассчета специфичности:

================================================

Комбинаторы

- descendant selector (space)
- child selector (>)
- adjacent sibling selector (+)
- general sibling selector (~)
  не имеют специфичности вообще, не оказывают влияния на общую специфичность

* {color: gray;}                  /* specificity = 0,0,0,0 */
h1 {color: red;}                  /* specificity = 0,0,0,1 */
p em {color: purple;}             /* specificity = 0,0,0,2 */
.grape {color: purple;}           /* specificity = 0,0,1,0 */
[data-text="Text"] {color: white;}/* specificity = 0,0,1,0 */
*.bright {color: yellow;}         /* specificity = 0,0,1,0 */
p.bright em.dark {color: maroon;} /* specificity = 0,0,2,2 */
#id216 {color: blue;}             /* specificity = 0,1,0,0 */
div#sidebar *[href] {color: silver;}  /* specificity = 0,1,1,1 */

<p style="color:red;">Text</p> /* specificity = 1,0,0,0 */

!important рассматривается отдельно от остальных и сравнивается специфичность
всех важных селекторов нацеленных на элемент
```

### Постер Specificity Wars

[Шпаргалка по расчету специфичности Specificity Wars](https://stuffandnonsense.co.uk/archives/css%5C_specificity%5C_wars.html)

## Каскадность и наследование

[https://developer.mozilla.org/ru/docs/Learn/CSS/Introduction\_to\_CSS/Cascade\_and\_inheritance](https://developer.mozilla.org/ru/docs/Learn/CSS/Introduction_to_CSS/Cascade_and_inheritance)

## Наследование

### Наследование и каскадирование

Механизм применения стилей не только к самим элементам, но и к их потомкам. От предка к потомкам (вниз по дереву, и никогда вверх)

Унаследованные свойства не имеют специфичности, даже нулевой. По этому универсальный селектор с нулевой специфичностью применяет свои стили.

### Правила каскадирования (книга)

1. Найти все правила содержащие селектор для данного элемента
2. Сортировать все объявления по весу. Свойства с !important имеют больший вес чем без.
3. Сортировать по происхождению объявлений стилей в порядке уменьшения. Есть три базовых происхождения стилей:
    1. Автор (создатель документа)
    2. Читатель
    3. Агент пользователя. В нормальных условиях стили автора побеждают стили читателя. !important стили читателя важнее чем любые другие стили включая !important стили автора. Оба и стили автора и стили читателя побеждают стили агента пользователя (браузера).
4. Сортировка по специфичности. Элементы с большей специфичностью имеют больший вес.
5. Сортировка по порядку расположения. Чем позже появляется объявление в таблицах стилей, тем больший вес им дается. Объявления которые были импортированы с помощью @import должны идти перед всеми остальными объявлениями таблицы стилей которая их импортирует.

### Порядок стилизации ссылок LVHA

Принцип сортировки по порядку расположения лежит в основе рекомендуемого порядка расположения стилей ссылок. Рекомендуется выстраивать ваши стили ссылок в порядке link-visited-hover-active или LVHA.

ОК, так каким образом псевдо-классы влияют на специфичность? Все они имеют равный вес, как оказывается. Так что следующие стили имеют одинаковую специфичность.

```css
a:link {color: blue;}        /* specificity = 1,1 */
a:active {color: red;}       /* specificity = 1,1 */
a:hover {color: magenta;}    /* specificity = 1,1 */
a:visited {color: purple;}   /* specificity = 1,1 */
```

Все из них могут применяться к гиперссылкам, и в некоторых случаях, могут применяться более одного. Например, непосещения ссылка `:link` может быть в состоянии наведения `:hover` и в активном состоянии `:active` в то же время, пока она еще не была посещена `:visited`. Так что три из указанных выше правил могут быть применены одновременно к гиперссылке, и все из селекторов имеют одинаковую специфичность, по этому последний из селекторов и применится к ссылке (в её конкретном состоянии). Следовательно стиль `:active` ни когда не появится, потому что он будет предопределен стилем `:hover`. Теперь представим что наша гиперссылка была посещена `:visited`. Она всё время будет фиолетовой, потому что селектор `:visited` перекрывает все другие состояния включая `:active` и `:hover` (из примера выше).

По этому рекомендованный порядок стилей для гиперссылок в спецификации [CSS1](https://www.w3.org/TR/CSS1/#anchor-pseudo-classes) следующий:

```css
a:link
a:visited
a:hover
a:active
```

Первые два могут идти в любом порядке (VLHA), потому что ссылка не может быть одновременно посещенной `:visited` и не посещенной `:link`.

Cпецификация [CSS2](https://www.w3.org/TR/2011/REC-CSS2-20110607/selector.html#dynamic-pseudo-classes) позволяет делать связки псевдо-классов. Например можно написать:

```css
a:visited:hover {color: maroon;} /* specificity = 2,1 */
a:link:hover {color: magenta;}   /* specificity = 2,1 */
a:hover:active {color: cyan;}    /* specificity = 2,1 */
```

Они имеют равную специфичность, но применяются к совершенно разным вариантам состояний ссылки. Можно получить комбинацию hover-active, например.

### Читать

#### Эрик Мейер Глава 3

#### Девид Макфарланд главы 4 и 5

[https://htmlacademy.ru/courses/66](https://htmlacademy.ru/courses/66)
[http://htmlbook.ru/samcss/nasledovanie](http://htmlbook.ru/samcss/nasledovanie)
[http://htmlbook.ru/samcss/kaskadirovanie](http://htmlbook.ru/samcss/kaskadirovanie)
