# Methods

## Методы конструктора

* [`Array.from()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/from) - Создает новый экземпляр `Array`из массивоподобного или итерируемого объекта.
* [`Array.isArray()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/isArray) - Возвращает`true`, если значение является массивом, иначе возвращает`false`.
* [`Array.observe()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/observe) - Асинхронно наблюдает за изменениями в массиве, подобно методу [`Object.observe()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Object/observe)для объектов. Метод предоставляет поток изменений в порядке их возникновения.
* [`Array.of()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/of) - Создает новый экземпляр`Array`с переменным количеством аргументов, независимо от числа или типа аргументов.

## Методы объекта

* **Методы изменения**
  * [`Array.prototype.copyWithin()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/copyWithin) - Копирует последовательность элементов массива внутри массива.
  * [`Array.prototype.fill()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/fill) - Заполняет все элементы массива от начального индекса до конечного индекса указанным значением.
  * [`Array.prototype.pop()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/pop) - Удаляет последний элемент из массива и возвращает его.
  * [`Array.prototype.push()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/push) - Добавляет один или более элементов в конец массива и возвращает новую длину массива.
  * [`Array.prototype.reverse()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/reverse) - Переворачивает порядок элементов в массиве — первый элемент становится последним, а последний — первым.
  * [`Array.prototype.shift()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/shift) - Удаляет первый элемент из массива и возвращает его.
  * [`Array.prototype.sort()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/sort) - Сортирует элементы массива на месте и возвращает отсортированный массив.
  * [`Array.prototype.splice()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/splice) - Добавляет и/или удаляет элементы из массива.
  * [`Array.prototype.unshift()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/unshift) - Добавляет один или более элементов в начало массива и возвращает новую длину массива.
* **Методы доступа**
  * [`Array.prototype.concat()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/concat) - Возвращает новый массив, состоящий из данного массива, соединенного с другим массивом и/или значением \(списком массивов/значений\).
  * [`Array.prototype.includes()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/includes) - Определяет, содержится ли в массиве указанный элемент, возвращая, соответственно, `true`или`false`.
  * [`Array.prototype.join()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/join) - Объединяет все элементы массива в строку.
  * [`Array.prototype.slice()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/slice) - Извлекает диапазон значений и возвращает его в виде нового массива.
  * [`Array.prototype.toSource()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/toSource) - Возвращает литеральное представление указанного массива; вы можете использовать это значение для создания нового массива. Переопределяет метод[`Object.prototype.toSource()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Object/toSource).
  * [`Array.prototype.toString()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/toString) - Возвращает строковое представление массива и его элементов. Переопределяет метод[`Object.prototype.toString()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Object/toString).
  * [`Array.prototype.toLocaleString()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/toLocaleString) - Возвращает локализованное строковое представление массива и его элементы. Переопределяет метод [`Object.prototype.toLocaleString()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Object/toLocaleString).
  * [`Array.prototype.indexOf()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/indexOf) - Возвращает первый \(наименьший\) индекс элемента внутри массива, равный указанному значению; или -1, если значение не найдено.
  * [`Array.prototype.lastIndexOf()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/lastIndexOf) - Возвращает последний \(наибольший\) индекс элемента внутри массива, равный указанному значению; или -1, если значение не найдено.
* **Методы обхода**
  * [`Array.prototype.forEach()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach) - Вызывает функцию для каждого элемента в массиве.
  * [`Array.prototype.entries()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/entries) - Возвращает новый объект итератора массива`Array Iterator`, содержащий пары ключей / значение для каждого индекса в массиве.
  * [`Array.prototype.every()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/every) - Возвращает`true`, если каждый элемент в массиве удовлетворяет условию проверяющей функции.
  * [`Array.prototype.some()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/some) - Возвращает`true`, если хотя бы один элемент в массиве удовлетворяет условию проверяющей функции.
  * [`Array.prototype.filter()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/filter) - Создаёт новый массив со всеми элементами этого массива, для которых функция фильтрации возвращает`true`.
  * [`Array.prototype.find()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/find) - Возвращает искомое значение в массиве, если элемент в массиве удовлетворяет условию проверяющей функции или[`undefined`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/undefined), если такое значение не найдено.
  * [`Array.prototype.findIndex()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/findIndex) - Возвращает искомый индекс в массиве, если элемент в массиве удовлетворяет условию проверяющей функции или -1, если такое значение не найдено.
  * [`Array.prototype.keys()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/keys) - Возвращает новый итератор массива, содержащий ключи каждого индекса в массиве.
  * [`Array.prototype.map()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/map) - Создаёт новый массив с результатами вызова указанной функции на каждом элементе данного массива.
  * [`Array.prototype.reduce()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce) - Применяет функцию к аккумулятору и каждому значению массива \(слева-направо\), сводя его к одному значению.
  * [`Array.prototype.reduceRight()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/reduceRight) - Применяет функцию к аккумулятору и каждому значению массива \(справа-налево\), сводя его к одному значению.
  * [`Array.prototype.values()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/values) - Возвращает новый объект итератора массива`Array Iterator`, содержащий значения для каждого индекса в массиве.
  * [`Array.prototype[@@iterator]()`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array/@@iterator) - Возвращает новый объект итератора массива`Array Iterator`, содержащий значения для каждого индекса в массиве.

