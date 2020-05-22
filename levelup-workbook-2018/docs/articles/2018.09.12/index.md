# Гипертекст, навигация (внутренняя и внешняя)

Jon Dukket 4 (стр. 81)

[Примеры кода](http://www.htmlandcssbook.com/code-samples/)

Ссылки — это определяющая функциональность веба, поскольку они позволяют вам переходить от одной странички, к другой и тем самым реализует идею веб браунинга или серфинга.

Наиболее частые типы ссылок:

- Ссылка с одного сайта на другой
- Ссылка с одной страницы на другую на этом же сайте
- Ссылки с одной части страницы на другую часть этой же страницы
- Ссылки которые открываются в новом окне браузера
- Ссылки которые запускают почтовый клиент с новым письмом и заполненным почтовым адресом

## [Элемент A](https://developer.mozilla.org/ru/docs/Web/HTML/Element/a) — anchor

```html
<a href="http://www.imdb.com">IMDB</a>
```

Текст внутри тегов называется текст ссылки.

Пишите понятные описания ссылок чтобы пользователь сразу сориентировался куда он переходит.

`href` — http-reference

URL — Uniform Recource Locator
URI — Uniform Recource Identificator

[В чем разница между URL и URI](http://qaru.site/questions/144/what-is-the-difference-between-a-uri-a-url-and-a-urn)

## Виды url

Абсолютный URL содержит полный путь к документу в сети

```html
<a href="https://ru.wikipedia.org/wiki/JPEG">JPEG</a>
```

Относительный URL содержит путь без указания домена, относительно текущего документа.

```html
<a href="/wiki/JPEG">JPEG</a>
```

### Виды относительных ссылок

В той же папке с текущим документом

```html
<a href="reviews.html">Reviews</a>
```

В директории-потомке

```html
<a href="music/listings.html">Listings</a>
```

В директории «внуке»

```html
<a href="movies/dvd/reviews.html"> Reviews</a>
```

В родительской директории (на уровень выше)

```html
<a href="../index.html">Home</a>
```

На несколько уровней выше

```html
<a href="../../index.html">Home</a>
```

### Почтовые ссылки mailto

```html
<a href="mailto:jon@example.org">Email Jon</a>
```

### Ссылки открывающиеся в новом окне

Используя атрибут [`target`](https://developer.mozilla.org/ru/docs/Web/HTML/Element/a#attr-target)

### Ссылка на конкретную часть страницы

```html
<a href="#arc_shot">Arc Shot</a>

<h1 id="arc_shot">Arc Shot</h1>
```

[Работа с файлами](https://developer.mozilla.org/ru/docs/Learn/Getting_started_with_the_web/Dealing_with_files)

### Резюме

- Ссылки создаются используя элемент `<a>`
- Для указания страницы на которую мы ссылаемся используется атрибут `href`
- Для ссылок на свой сайт лучше использовать относительные URL
- Вы можете создать ссылки которые открывают почтовый клиент с заполненным полем «Кому» с `mailto:`
- Можно использовать атрибут `id` для указания элементов внутри страницы на который можно сделать ссылку

## Медиаконтент, форматы графики

Есть множество причин, почему вы хотите добавить картинку на сайт: показать логотип, фотографию, иллюстрацию, диаграмму или график.

Цель раздела — научиться:

- Вставлять изображения в HTML документ
- Выбирать правильный формат изображения
- Показывать картинку в правильном размере
- Оптимизировать изображения для ускорения загрузки

Также для размещения изображений можно использовать CSS-свойство background-image с которым мы познакомимся на занятиях по CSS

## Медиаконтент

Лучше один раз увидеть, чем сто раз услышать. Хорошие картинки помогают отличать хорошо выглядящий сайт от средненького.

### Где брать картинки

Фотостоки:

- [unsplash.com](https://unsplash.com) — free
- [www.pexels.com](https://www.pexels.com/) — free
- [www.istockphoto.com](https://www.istockphoto.com/)
- [www.gettyimages.com](https://www.gettyimages.com/)
- [ua.depositphotos.com](https://ua.depositphotos.com/)
- [www.shutterstock.com/ru](https://www.shutterstock.com/ru/)
- [ru.fotolia.com](https://ru.fotolia.com/)
- [Google Photostock](https://www.google.com.ua/search?q=photostock&oq=photostock&aqs=chrome..69i57j0l5.1957j0j1&sourceid=chrome&ie=UTF-8)

### Глубина цвета

[Глубина цвета](https://www.google.com.ua/search?q=image+bit+depth&client=safari&rls=en&dcr=0&tbm=isch&source=iu&pf=m&ictx=1&fir=cP8fYywtgLPCAM%253A%252Cy3o64zdKZPyjLM%252C_&usg=__R7o8CxZ4yGX9UJ5QVKH0T8v1ueE%3D&sa=X&ved=0ahUKEwiw9cu89IDXAhXM2xoKHZj0DmwQ9QEISTAE&biw=2326&bih=1247#imgrc=IgQdO7NwGUeUCM:) (Google)

[Глубина цвета](https://ru.wikipedia.org/wiki/%D0%93%D0%BB%D1%83%D0%B1%D0%B8%D0%BD%D0%B0_%D1%86%D0%B2%D0%B5%D1%82%D0%B0) Wikipedia

[Developers Guide to Images](https://www.jessechapo.com/posts/Developers-Guide-to-Images.html)

### Цветовые модели

#### Аддиттивная

![RGB](/articles/2018.09.12/RGB.png)

#### Субтрактивная

![CMYK](/articles/2018.09.12/CMYK.png)

### Цветовые профили (охват)

[https://furbo.org/color/Colorful/](https://furbo.org/color/Colorful/) тест цвета

[DCI-P3](https://ru.wikipedia.org/wiki/DCI-P3) Wikipedia

[DCI-P3 демо](https://webkit.org/blog-files/color-gamut/comparison.html)

DCI-P3 дает на 25% больший цветовой охват

[Пример фото с широким цветовым охватом](https://furbo.org/color/WideGamut/)

Детальней на курсе CSS

#### sRGB

[https://www.w3.org/TR/css-color-3/#rgb-color](https://www.w3.org/TR/css-color-3/#rgb-color)

[https://furbo.org/color/Colorful/](https://furbo.org/color/Colorful/)

### Форматы графики

#### [JPEG](https://ru.wikipedia.org/wiki/JPEG)

Используется для фотографий или других видов изображений с плавными переходами между цветами. Не поддерживает прозрачность.

Магическое число для значения качества в диапазоне **60–85**. Больше 85 вы уже не заметите разницу на глаз, меньше 60 будет выглядеть плохо.

[ImageOptim](https://imageoptim.com/versions.html) — Mac
[FileOptimizer](https://sourceforge.net/projects/nikkhokkho/) — Windows

#### [JPEG XR](https://uk.wikipedia.org/wiki/JPEG_XR) — от Microsoft

[https://caniuse.com/#feat=jpegxr](https://caniuse.com/#feat=jpegxr)

#### JPEG 2000 — Apple

[https://caniuse.com/#feat=jpeg2000](https://caniuse.com/#feat=jpeg2000)

#### PNG

Подходит для изображений с «плоскими» цветами и резкими краями, как логотипы и иллюстрации без градиентов. Может иметь один или множество уровней прозрачности.

альфа прозрачность

#### APNG анимированный png

[http://caniuse.com/#search=apng](http://caniuse.com/#search=apng)

#### [WEBP](https://ru.wikipedia.org/wiki/WebP)

[https://developers.google.com/web/fundamentals/design-and-ux/responsive/images?hl=ru](https://developers.google.com/web/fundamentals/design-and-ux/responsive/images?hl=ru)
[http://caniuse.com/#search=webp](http://caniuse.com/#search=webp)

[сравнение анимационных форматов](http://littlesvr.ca/apng/gif_apng_webp.html)

#### [GIF](https://ru.wikipedia.org/wiki/GIF)

Старый формат графики. Можно считать что он утратил свою актуальность на сейчас.

- прозрачность — один уровень (без альфа прозрачности)
- 256 цветов
- анимация — единственный повод применять GIF

#### [SVG](https://ru.wikipedia.org/wiki/SVG) — Scalable vector graphics

Масштабируемая векторная графика для веб — подмножество языка XML, как следствие, такая графика доступна для манипуляций через CSS и JavaScript, и хорошо анимируется.

Это, можно сказать, «отдельная область знаний», для которой есть отдельные специалисты.

[SVG Tutorial](https://developer.mozilla.org/ru/docs/Web/SVG/Tutorial)

[https://htmlacademy.ru/courses/130](https://htmlacademy.ru/courses/130) — курс для ознакомления по желанию

##### Оптимизация SVG

[https://jakearchibald.github.io/svgomg/](https://jakearchibald.github.io/svgomg/)

##### Демки SVG

[Демо по svg рисованию](http://svgjs.com/svg.draw.js/demo/index.html)

[Динамические формы при помощи SVG](https://tympanus.net/codrops/2017/10/17/dynamic-shape-overlays-with-svg/)

`fill: red;` — покрасить цветом внутри path
`stroke: blue` — покрасить контур

[https://tympanus.net/Development/ShapeMorphIdeas/index3.html](https://tympanus.net/Development/ShapeMorphIdeas/index3.html)

[https://tympanus.net/codrops/2017/08/08/morphing-page-transition/](https://tympanus.net/codrops/2017/08/08/morphing-page-transition/)

[https://codepen.io/collection/XLebem/](https://codepen.io/collection/XLebem/) — комплект SVG демок на anime.js

[http://animejs.com](http://animejs.com)

[http://dmitrybaranovskiy.github.io/raphael/](http://dmitrybaranovskiy.github.io/raphael/)

[https://htmlacademy.ru/blog/127-a-guide-to-svg-on-web](https://htmlacademy.ru/blog/127-a-guide-to-svg-on-web)

[https://svgvspng.com/#ru](https://svgvspng.com/#ru)

Вставка картинок [https://webref.ru/layout/html5-css3/img](https://webref.ru/layout/html5-css3/img)

## Оптимизация изображений

- [Оптимизация изображений](https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/image-optimization?hl=ru)
- [https://images.guide/](https://images.guide/) by Addy Osmani