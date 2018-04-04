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

С выходом ECMAScript 6 появился целый набор ключевых слов, реализующих [классы](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes). Они могут показаться знакомыми людям, изучавшим языки, основанные на классах, но есть существенные отличия. JavaScript был и остаётся прототипно-ориентированным языком. Новые ключевые слова: "`class`", "`constructor`", "`static`", "`extends`" и "`super`".

