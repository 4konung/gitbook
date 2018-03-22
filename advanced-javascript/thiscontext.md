# Контекст выполнения

Поведение ключевого слова `this` в  JavaScript несколько отличается по сравнению с остальными языками. Имеются также различия при использовании `this` в [строгом](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Strict_mode) и нестрогом режиме.

В большинстве случаев значение `this` определяется тем, каким образом вызвана функция. Значение `this`не может быть установлено путем присваивания во время исполнения кода и может иметь разное значение при каждом вызове функции. В ES5 представлен метод [`bind`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/bind), чтобы [определить значение ключевого слова this независимо от того, как вызвана функция](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this$translate?tolocale=ru#The_bind_method). Также в ECMAScript 2015 представлены [стрелочные функции](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Functions/Arrow_functions), this которых привязан к окружению, в котором была создана стрелочная функция.

---

## Глобальный контекст {#Глобальный_контекст}



