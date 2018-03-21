# Цикл `while`

Цикл [`while`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Statements/while)выполняет выражения пока условие истинно. Выглядит он так:

```js
while (условие)
  выражения
```

Если `условие` становится ложным, выражения в цикле перестают выполняться и управление переходит к выражению после цикла.

`Условие`проверяется на истинность до того, как выполняются `выражения` в цикле. Если `условие`истинно, выполняются `выражения`, а затем условие проверяется снова. Если `условие` ложно, выполнение приостанавливается и управление переходит к выражению после `while`.

Пример:

```js
var n = 0;
var x = 0;
while (n < 3) {
  n++;
  x += n;
}
```

С каждой итерацией, цикл увеличивает `n`и добавляет это значение к `x`. Поэтому, `x`и `n` получают следующие значения:

* После первого прохода: `n`= 1 и`x`= 1
* После второго:`n`= 2 и`x`= 3
* После третьего прохода:`n`= 3 и`x`= 6


