# cards

## Project setup

```
npm install
```

### Compiles and hot-reloads for development

```
npm run serve
```

### Compiles and minifies for production

```
npm run build
```

### Customize configuration

See [Configuration Reference](https://cli.vuejs.org/config/).

### Ответы на вопросы:

1. Каким будет результат следующей операции на языке JavaScript: [1, 2, 3] + [4, 5, 6]. Почему был получен такой результат?

- Ответ: 1,2,34,5,6 - результат будет такой, так как + выполняет сложение чисел и конкатенацию строк. Если любой из ее операндов оказывается объектом, то он преобразует его в элементарное значение, примитив. После получения двух элементарных значений проверяются их типы и, если один из аргументов является строкой, тогда другой преобразовывается в строку и выполняется конкатенация строк, таким образом, массив преобразуется в строку

2. Дано выражение:
   var a = {b: 1};
   var b = a;
   b.b = 2;
   console.log(a);
   Что будет выведено в консоли? Почему был получен такой результат?

- Ответ: в консоли будет выведено 2, т.к. объекты - это ссылочный тип данных и он отправляет ссылку в а, при этом сам объект изменять нельзя, но можно изменять поля объекта, соответсвенно, изменив поле b.b = 2 в b, b - передает ссылку в объект а и поле b в объекте а также изменяется на значение 2, итого и в а и в b - поле b будет иметь значение 2

3. Написать регулярное выражение, совпадающее с числом с плавающей точкой с точностью до 3 знака после запятой.

- Ответ: /^[0-9]\*\.[0-9]{3}$/gm

```javascript
;/^[0-9]*\.[0-9]{3}$/gm
console.log('0', /^[0-9]*\.[0-9]{3}$/gm.test(1)) // false
console.log('1', /^[0-9]*\.[0-9]{3}$/gm.test(1.1)) // false
console.log('2', /^[0-9]*\.[0-9]{3}$/gm.test(1.111)) // true
console.log('3', /^[0-9]*\.[0-9]{3}$/gm.test(1.1111)) // false
```

4. Написать регулярное выражение, по которому определяется является ли строка ссылкой. Объяснить, как оно работает. Пример:

```javascript
  const isURL = str => true
  isURL(‘https://example.com’)
  isURL(‘http://www.example.com’)
```

- Ответ: регулярное выражение, где посимвольно прописывается, что допустимо, а что нет

```javascript
function isURL(url) {
  const regexp =
    /^https?:\/\/(?:www\.)?[-a-zA-Z0-9@:%._\+~#=]{1,256}\.[a-zA-Z0-9()]{1,6}\b(?:[-a-zA-Z0-9()@:%_\+.~#?&\/=]*)$/
  return regexp.test(url)
}
console.log(isURL('https://example.com')) // true
console.log(isURL('https://examplecom')) // false
console.log(isURL('http://www.example.com')) // true
```

5. Каким будет значение переменной text после выполнения данного JavaScript кода? Опишите, почему получился такой результат.

```javascript
function setText(message) {
  text = message
}
var text = 'Текст'
setText('Сообщение')
```

- Ответ: значение text будет = Сообщение, т.к. переменная text, объявленная с помощью var имеет функциональную область видимости, поэтому к ней есть доступ внутри функции setText, если же была бы переменная, обяъвленная с помощью let, то была бы ошибка RefereceError, т.к. let имеет блочную область видимости, соответственно доступна только в пределах блока.
  При всем этом в setText мы передали 'Сообщение'.

6. Написать функцию для получения списка всех артикулов товаров в консоли браузера на странице https://groupprice.ru/categories/jenskaya-odejda?referer_from=main_catalog

- Ответ:

```javascript
function getArticles() {
  const product = document.querySelectorAll('._product')
  const articles = []
  product.forEach((item) => {
    articles.push(item.getAttribute('data-id'))
  })
  return articles
}
getArticles()
```

7. Написать функцию для получения всех характеристик товара в консоли браузера в виде объекта в формате attributeName: value на странице https://nir-vanna.ru/product/smesitel-bravat-art-f175109c-dlya-rakoviny/

- Ответ:

```javascript
function getSettings() {
  const result = []
  const settings = document.querySelectorAll('.tab-pane-product-parameter-item')
  settings.forEach((item) => {
    const attributeName = item
      .getElementsByClassName('parameter-name')[0]
      .innerText.replace(/ [ \r\n]+/gm, '')
      .replace(/[\n\r]+/g, '')
    const value = item
      .getElementsByClassName('parameter-value')[0]
      .innerText.replace(/ [ \r\n]+/gm, '')
      .replace(/[\n\r]+/g, '')
    result.push({ attributeName, value })
  })
  return result
}
getSettings()
```
