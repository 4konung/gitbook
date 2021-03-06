# Функции

Функция – это фрагмент исполняемого кода, который определен в JavaScript программе или заранее предопределен в реализации JavaScript. Хотя функция определяется только один раз, JavaScript программа может исполнять или вызывать ее сколько угодно. Функции могут передаваться аргументы, или параметры, определяющие значение или значения, для которых она должна выполнять вычисления; также функция может возвращать значение, представляющее собой результат этих вычислений. Реализации JavaScript предоставляют много предопределенных функций, таких как функция Math.sin\(\), возвращающая синус угла.

JavaScript программы могут также определять собственные функции, содержащие, например, такой код:

```js
function square(x) { // Функция называется square. Она принимает один аргумент, x.
 // Здесь начинается тело функции.
 return x*x; // Функция возводит свой аргумент в квадрат и возвращает
 // полученное значение.
} // Здесь функция заканчивается.
```

Определив функцию, можно вызывать ее, указав имя, за которым следует заключенный в скобки список необязательных аргументов, разделенных запятыми. Следующие строки представляют собой вызовы функций:

```js
y = Math.sin(x);
y = square(x);
d = compute_distance(x1, y1, z1, x2, y2, z2);
move();
```

Важной чертой JavaScript является то, что функции представляют собой значения, которыми можно манипулировать в JavaScript коде. Во многих языках, в том числе в Java, функции – это всего лишь синтаксические элементы языка, но не тип данных: их можно определять и вызывать.  То обстоятельство, что функции в JavaScript представляют собой настоящие значения, придает языку большую гибкость. Это означает, что функции могут храниться в переменных, массивах и объектах, а также передаваться в качестве аргументов другим функциям. Очень часто это бывает очень удобно.

Поскольку функции представляют собой значения, такие же, как числа и строки, они могут присваиваться свойствам объектов. Когда функция присваивается свойству объекта, она часто называется методом этого объекта. Методы – важная часть объектноориентированного программирования.

---

## Содержание

1. [Основы](/js-basics/functions/basics.md)
2. [Методы](/js-basics/functions/methods.md)
3. [Примеры](/js-basics/functions/examples.md)
4. [Задания](/js-basics/functions/test-yourself.md)
5. [Ссылки на дополнительные источники](/js-basics/functions/references.md)



