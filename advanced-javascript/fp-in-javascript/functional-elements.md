# Функциональные элементы в JavaScript

### **Анонимные функции**

Анонимная функция – это функция, которая определяется без идентификатора. В JavaScript эта концепция уже настроена. Если вы использовали JavaScript не только для наипростейших задач, я уверен, что вы тоже знаете о нем. Когда вы используете jQuery, вот что вы точно печатаете сначала:

```js
$(document).ready(function () {
    //do some stuff
});
```

Функция, переданная в $\(document\).ready и есть анонимной функцией. Этот концепт очень выгодный в некоторых случаях, когда мы хотим действовать за принципом DRY \(Don't repeat yourself; if you're repeating yourself, you're doing it wrong\).

---

### **Функции высшего порядка**

Функции высшего порядка – это функции, которые принимают функции в качестве аргументов или возвращают функции. Мы можем возвратить и провести функции, как аргументы в C\#, Java 8, Python, Perl, Ruby… Самый известный язык программирования – JavaScript имеет эти встроенные функции уже очень давно. Вот стандартный пример:

```js
function animate(property, duration, endCallback) {
    //Animation here...
    if (typeof endCallback === 'function') {
        endCallback.apply(null);    }
}
animate('background-color', 5000, function () {
    console.log('Animation finished');
});
```

В коде выше есть функция animate. Она принимает в качестве свойств аргументов, которые должны быть анимированными, продолжительность и колбек, к которым мы должны ссылаться, когда анимация будет завершена. Мы также имеем этот пример в jQuery. Есть множество методов jQuery, которые принимают функции как аргументы, например $.get:

```js
$.get('http://example.com/test.json', function (data) {
    //processing of the data
});
```

Есть еще один вид функций высшего порядка – такие, которые возвращают функции. Есть много случаев в JavaScript, когда возврат функции – большой шаг вперед. Например, когда мы хотим использовать кэширование:

```js
lz.memo = function (fn) {
    var cache = {};
    return function () {
        var key = [].join.call(arguments, '§') + '§';
        if (key in cache) {
            return cache[key];
        }
        return cache[key] = fn.apply(this, arguments);
    };
};
```

У нас есть переменный кэш в локальных пределах функции-родителя. В каждом вызове сначала будет проверено, была ли функция уже вызвана этими аргументами, если да, то результат будет возвращен немедленно, иначе его кэшируют и возвратят. Представьте такой случай:

```js
var foo = 1;
function bar(baz) {
    return baz + foo;
}
var cached = lz.memo(bar);
cached(1); //2
foo += 1;
cached(1); //2
```

У нас есть функция bar, которая принимает единый аргумент – baz и возвращает сумму baz и global foo. Когда мы используем memo, мы готовим bar к кэшированию и сохраняем ссылку на кэшированную копию в переменной cashed. Когда мы вызываем переменную cashed впервые, она исчисляется аргументом 1, ее тело вызывается и поэтому результатом будет 2. После этого мы повышаем foo и вызываем cashed снова. Теперь у нас одинаковый результат \(как и должно быть в чисто функциональных языках\), но это неправильный результат.

Это случается потому, что у нас есть некоторое подобие состояния. Состояние – это нечто, что в последнее время относят к разделу монад \(не одинакового вида состояния\).

---

### **Замыкания**

Давайте снова посмотрим на memo. У нас есть переменная cashed, она определена в лексической области функции, которая возвращает кэшированную функцию. Эта переменная также доступна с возвращенной функции, потому что создано замыкание. Это еще один элемент из функционального программирования. И он весьма распространен. Еще один способ для реализации приватности в JavaScript – это использование замыканий:

```js
var timeline = (function () {
    var articles = [];
    function sortArticles() {
        articles.sort(function (a, b) {
            return a.name - b.name;
        });
    }
    return {
        getArticles: function () {
            return articles;
        },
        setArticles: function (articleList) {
           articles = articleList;
           sortArticles();
        }
    };
}());
```

В примере выше был объект, который называется таймлайн. Это результат немедленно вызываемых функций \(IIFE\) которые возвращают объект со свойствами getArticles и setArticles, которые представляют текущий публичный интерфейс таймлайна. Внутри лексической области IIFE есть определение массива articles и функция сортировки, которую нельзя вызвать прямо используя объект таймлайна.

---

### **Рекурсия**

Еще один элемент, одинаковый почти во всех языках программирования – рекурсия. Это функция, которая вызывает себя из себя же самой:

```js
function factorial(n) {
    if (n <= 1) return 1;
    return n * factorial(n - 1);
}
```

Выше – базовый пример, который показывает имплементацию факториала с использованием рекурсии.

### **Управление состояниями \(Монады\)**

Обычно, чисто функциональные языки программирования как Haskell управляют состояниями с помощью монад. Вот реализации монад в JavaScript. Возьмем пример Douglas Crockford:

```js
/* Code by Douglas Crockford */
function MONAD(modifier) {
    'use strict';
    var prototype = Object.create(null);
    prototype.is_monad = true;
    function unit(value) {
        var monad = Object.create(prototype);
        monad.bind = function (func, args) {
            return func.apply(
                undefined,
                [value].concat(Array.prototype.slice.apply(args || []))
            );
        };
        if (typeof modifier === 'function') {
            modifier(monad, value);
        }
        return monad;
    }
    unit.method = function (name, func) {
        prototype[name] = func;
        return unit;
    };
    unit.lift_value = function (name, func) {
        prototype[name] = function () {
            return this.bind(func, arguments);
        };
        return unit;
    };
    unit.lift = function (name, func) {
        prototype[name] = function () {
            var result = this.bind(func, arguments);
            return result && result.is_monad === true ? result : unit(result);
        };
        return unit;
    };
    return unit;
}
```

Пример, который показывает, как мы можем создать I/O монаду:

```js
var monad = MONAD();
monad(prompt("Enter your name:")).bind(function (name) {
    alert('Hello' + name + '!');
});
```



