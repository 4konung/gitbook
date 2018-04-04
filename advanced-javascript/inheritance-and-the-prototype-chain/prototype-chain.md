## Способы создания объектов и получаемые в итоге цепочки прототипов {#Различные_способы_создания_объектов_и_получаемые_в_итоге_цепочки_прототипов}

### Создание объектов с помощью литералов {#Создание_объектов_с_помощью_литералов}

```js
var o = {a: 1};

// Созданный объект 'o' имеет Object.prototype в качестве своего [[Prototype]]
// у 'o' нет собственного свойства 'hasOwnProperty'
// hasOwnProperty — это собственное свойство Object.prototype. 
// Таким образом 'o' наследует hasOwnProperty от Object.prototype
// Object.prototype в качестве прототипа имеет null.
// o ---> Object.prototype ---> null

var a = ["yo", "whadup", "?"];

// Массивы наследуются от Array.prototype 
// (у которого есть такие методы, как indexOf, forEach и т.п.).
// Цепочка прототипов при этом выглядит так:
// a ---> Array.prototype ---> Object.prototype ---> null

function f(){
  return 2;
}

// Функции наследуются от Function.prototype 
// (у которого есть такие методы, как call, bind и т.п.):
// f ---> Function.prototype ---> Object.prototype ---> null
```

### Создание объектов с помощью конструктора {#Создание_объектов_с_помощью_конструктора}

В JavaScript "конструктор" — это "просто" функция, вызываемая с оператором [new](https://developer.mozilla.org/en/JavaScript/Reference/Operators/new).

```js
function Graph() {
  this.vertexes = [];
  this.edges = [];
}

Graph.prototype = {
  addVertex: function(v){
    this.vertexes.push(v);
  }
}

var g = new Graph();
// объект 'g' имеет собственные свойства 'vertexes' и 'edges'.
// g.[[Prototype]] принимает значение Graph.prototype при выполнении new Graph().
```

### Object.create {#Object.create}

В ECMAScript 5 представлен новый метод создания объектов: [Object.create](https://developer.mozilla.org/en/JavaScript/Reference/Global_Objects/Object/create). Прототип создаваемого объекта указывается в первом аргументе этого метода:

```js
var a = {a: 1}; 
// a ---> Object.prototype ---> null

var b = Object.create(a);
// b ---> a ---> Object.prototype ---> null
console.log(b.a); // 1 (унаследовано)

var c = Object.create(b);
// c ---> b ---> a ---> Object.prototype ---> null

var d = Object.create(null);
// d ---> null
console.log(d.hasOwnProperty); 
// undefined, т.к. 'd' не наследуется от Object.prototype
```

### Используя ключевое слово`class` {#Используя_ключевое_слово_class}

С выходом ECMAScript 6 появился целый набор ключевых слов, реализующих [классы](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes). Они могут показаться знакомыми людям, изучавшим языки, основанные на классах, но есть существенные отличия. JavaScript был и остаётся прототипно-ориентированным языком. Новые ключевые слова: "`class`", "`constructor`", "`static`", "`extends`" и "`super`".

```js
"use strict";

class Polygon {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
}

class Square extends Polygon {
  constructor(sideLength) {
    super(sideLength, sideLength);
  }
  get area() {
    return this.height * this.width;
  }
  set sideLength(newLength) {
    this.height = newLength;
    this.width = newLength;
  }
}

var square = new Square(2);
```

### Производительность {#Производительность}

Длительное время поиска свойств, располагающихся относительно высоко в цепочке прототипов, может негативно сказаться на производительности \(performance\), особенно в критических в этом смысле местах кода. Кроме того, попытка найти несуществующие свойства неизбежно приведёт к проверке на их наличие у всех объектов цепочки прототипов.

Кроме того, при циклическом переборе свойств объекта будет обработано каждое свойство, присутствующее в цепочке прототипов.

Если вам необходимо проверить, определено ли свойство у_самого объекта_, а не где-то в его цепочке прототипов, вы можете использовать метод[`hasOwnProperty`](https://developer.mozilla.org/ru/docs/JavaScript/Reference/Global_Objects/Object/hasOwnProperty), который все объекты наследуют от`Object.prototype`.

[`hasOwnProperty`](https://developer.mozilla.org/ru/docs/JavaScript/Reference/Global_Objects/Object/hasOwnProperty)— единственная существующая в JavaScript возможность работать со свойствами, не затрагивая цепочку прототипов.

### Плохая практика: расширение базовых прототипов {#Плохая_практика_расширение_базовых_прототипов}

Одной из частых ошибок является расширение`Object.prototype`или других базовых прототипов.

Такой подход называется monkey patching и нарушает принцип _инкапсуляции_. Несмотря на то, что ранее он использовался в таких широко распространенных фреймворках, как например, Prototype.js, в настоящее время не существует разумных причин для его использования, поскольку в данном случае встроенные типы "захламляются" дополнительной нестандартной функциональностью.

Единственным оправданием расширения базовых прототипов могут являться лишь полифиллы - эмуляторы новой функциональности \(например,`Array.forEach)` для не поддерживающих её реализаций языка в старых веб-броузерах.

