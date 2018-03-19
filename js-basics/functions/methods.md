## Методы конструктора

Глобальный объект`Function`не имеет собственных методов или свойств, однако, поскольку он сам является функцией, он наследует некоторые методы и свойства через цепочку прототипов объекта[`Function.prototype`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Function/prototype).

---

## Методы объекта

* [`Function.prototype.apply()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Function/apply) - Вызывает функцию и устанавливает **`this`**в контекст предоставленного значения; аргументы передаются объектом[`Array`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array).

* [`Function.prototype.bind()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Function/bind) - Создаёт новую функцию, которая, при вызове, самостоятельно вызывает эту функцию в контексте предоставленного значения, с данной последовательностью аргументов, предшествующих любым аргументам, переданным в новую функцию при её вызове. Устанавливает **`this`**в контекст предоставленного значения.

* [`Function.prototype.call()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Function/call) - Вызывает \(выполняет\) функцию и устанавливает**`this `**в контекст предоставленного значения; аргументы передаются как есть.

* [`Function.prototype.isGenerator()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Function/isGenerator) - Возвращает`true`, если функция является [генератором](https://developer.mozilla.org/ru/docs/Web/JavaScript/Guide/Iterators_and_Generators); в противном случае возвращает `false`.

* [`Function.prototype.toSource()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Function/toSource) - Возвращает строку, представляющую исходный код функции. Переопределяет метод [`Object.prototype.toSource`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Object/toSource).

* [`Function.prototype.toString()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Function/toString) - Возвращает строку, представляющую исходный код функции. Переопределяет метод[`Object.prototype.toString`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Object/toString).





