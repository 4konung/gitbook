# Basics

## Логические значения

Логические значения обычно представляют собой результат сравнений, выполняемых в JavaScript-программах. Например:

```javascript
a == 4
```

Это выражение проверяет, равно ли значение переменной _**a**_ числу 4. Если да, результатом этого сравнения будет логическое значение _true_. Если переменная _a_ не равна 4, результатом сравнения будет false.

Логические значения обычно используются в управляющих конструкциях JavaScript. Например, инструкция if/else в JavaScript выполняет одно действие, если логическое значение равно true, и другое действие, если false. Обычно сравнение, создающее логическое значение, непосредственно объединяется с инструкцией, в которой оно используется. Результат выглядит таким образом:

```javascript
if (a == 4) {
 b = b + 1;
} else {
 a = a + 1;
}
```

Здесь выполняется проверка, равна ли переменная _a_ числу 4. Если да, к значению переменной _b_ добавляется 1; в противном случае число 1 добавляется к значению переменной _a_.

## Преобразование логических значений

Логические значения легко преобразуются в значения других типов, причем нередко такое преобразование выполняется автоматическим образом. Если логическое значение используется в числовом контексте, значение true преобразуется в число 1, а false – в 0. Если логическое значение используется в строковом контексте, тогда значение true преобразуется в строку "true", а false – в строку "false".

Когда в качестве логического значения используется число, оно преобразуется в значение _true_, если оно не равно значениям 0 или NaN, которые преобразуются в логическое значение _false_. Когда в качестве логического значения используется строка, она преобразуется в значение true, если это не пустая строка, в противном случае в результате преобразования получается значение false. Специальные значения null и undefined преобразуются в false, а любые функция, объект или массив, значения которых отличны от null, преобразуются в true.

Если вы предпочитаете выполнять преобразование явно, можно воспользоваться функцией Boolean\(\):

```javascript
var x_as_boolean = Boolean(x);
```

Другой способ явного преобразования заключается в использовании двойного оператора логического отрицания:

```javascript
var x_as_boolean = !!x;
```

