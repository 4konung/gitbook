## Стандартные встроенные объекты

В JavaScript есть несколько объектов, встроенных в ядро, например[`Math`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Math),[`Object`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Object),[`Array`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array) и[`String`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/String). Пример ниже показывает как использовать объект Math, чтобы получить случайное число, используя его метод random\(\).

```js
console.log(Math.random());
```

Каждый объект в JavaScript является экземпляром объекта [`Object`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Object), следовательно наследует все его свойства и методы \(исключение, результат вызова Object.create\(null\)\). 

