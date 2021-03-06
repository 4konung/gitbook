# Basics

Хотя JavaScript поддерживает тип данных, который мы называем объектом, в нем нет формального понятия класса. Это в значительной степени отличает его от классических объектно-ориентированных языков программирования, таких как C++ и Java. Общая черта объектно-ориентированных языков – это их строгая типизация и поддержка механизма наследования на базе классов. По этому критерию JavaScript легко исключить из числа истинно объектно-ориентированных языков. С другой стороны, мы видели, что JavaScript активно использует объекты и имеет особый тип наследования на базе прототипов. JavaScript – это истинно объектно-ориентированный язык. Он был реализован под влиянием некоторых других \(относительно малоизвестных\) объектно-ориентированных языков, в которых. вместо наследования, на основе классов реализовано наследование на базе прототипов.Несмотря на то, что JavaScript – это объектно-ориентированный язык, не базирующийся на классах, он неплохо имитирует возможности языков на базе классов, таких как Java и C++.

Объект, как мы уже видели, – это структура данных, которая содержит различные фрагменты именованных данных, а также может содержать методы для работы с этими фрагментами данных. Объект группирует связанные значения и методы в единый удобный набор, который, как правило, облегчает процесс программирования, увеличивая степень модульности и возможности многократного использования кода. Объекты в JavaScript могут иметь произвольное число свойств, и свойства могут добавляться в объект динамически. В строго типизированных языках, таких как Java и C++, это не так. В них любой объект имеет предопределенный набор свойств, а каждое свойство имеет предопределенный тип. Имитируя объектно-ориентированные приемы программирования при помощи JavaScript- объектов, мы, как правило, заранее определяем набор свойств для каждого объекта и тип данных, содержащихся в каждом свойстве.

В Java и C++ класс определяет структуру объекта. Класс точно задает поля, которые содержатся в объекте, и типы данных этих полей. Он также определяет методы для работы с объектом. В JavaScript нет формального понятия класса, но, как мы видели, в этом языке приближение к возможностям классов реализуется с помощью конструкторов и объектов-прототипов.

И JavaScript, и объектно-ориентированные языки, основывающиеся на классах, допускают наличие множества объектов одного класса. Мы часто говорим, что объект – это экземпляр класса. Таким образом, одновременно может существовать множество экземпляров любого класса. Иногда для описания процесса создания объекта \(т. е. экземпляра класса\) используется термин создание экземпляра.

## Свойства экземпляра

Каждый объект имеет собственные копии свойств экземпляра. Другими словами, если имеется 10 объектов данного класса, то имеется и 10 копий каждого свойства экземпляра. Например, в нашем классе _**Rectangle **_любой объект _**Rectangle **_имеет свойство _width_, определяющее ширину прямоугольника. В данном случае _width _представляет собой свойство экземпляра. А поскольку каждый объект имеет собственную копию свойства экземпляра, доступ к этим свойствам можно получить через отдельные объекты. Если, например, r – это объект, представляющий собой экземпляр класса _**Rectangle**_, мы можем получить его ширину следующим образом:

```javascript
r.width
```

По умолчанию любое свойство объекта в JavaScript является свойством экземпляра. Однако, чтобы по-настоящему имитировать объектно-ориентированное программирование, мы будем говорить, что свойства экземпляра в JavaScript – это те свойства, которые создаются и/или инициализируются функцией-конструктором.

## Методы экземпляра

Метод экземпляра во многом похож на свойство экземпляра, за исключением того, что это метод, а не значение. Методы экземпляра вызываются по отношению к определенному объекту, или экземпляру. Метод _area\(\)_ нашего класса Rectangle представляет собой метод экземпляра. Он вызывается для объекта _**Rectangle **_следующим образом:

```javascript
a = r.area( );
```

Методы экземпляра ссылаются на объект или экземпляр, с которым они работают, при помощи ключевого слова _this_. Метод экземпляра может быть вызван для любого экземпляра класса, но это не значит, что каждый объект содержит собственную копию метода, как в случае свойства экземпляра. Вместо этого каждый метод экземпляра совместно используется всеми экземплярами класса. В JavaScript мы определяем метод экземпляра класса путем присваивания функции свойству объекта-прототипа в конструкторе. Так, все объекты, созданные данным конструктором, совместно используют унаследованную ссылку на функцию и могут вызывать ее с помощью приведенного синтаксиса вызова методов.

## Свойства класса

Свойство класса – это свойство, связанное с самим классом, а не с каждым экземпляром этого класса. Независимо от того, сколько создано экземпляров класса, есть только одна копия каждого свойства класса. Так же, как свойства экземпляра доступны через экземпляр класса, доступ к свойствам класса можно получить через сам класс. Запись Number.MAX\_VALUE – это пример обращения к свойству класса в JavaScript, означающий, что свойство MAX\_VALUE доступно через класс Number. Так как имеется только одна копия каждого свойства класса, свойства класса по существу являются глобальными. Однако их достоинство состоит в том, что они связаны с классом и имеют логичную нишу, позицию в пространстве имен JavaScript, где они вряд ли будут перекрыты другими свойствами с тем же именем. Очевидно, что свойства класса имитируются в JavaScript простым определением свойства самой функции-конструктора. Например, свойство класса Rectangle.UNIT для хранения единичного прямоугольника с размерами 1x1 можно создать так:

```javascript
Rectangle.UNIT = new Rectangle(1,1);
```

Здесь Rectangle – это функция-конструктор, но, поскольку функции в JavaScript представляют собой объекты, мы можем создать свойство функции точно так же, как свойства любого другого объекта.

## Методы класса

Метод класса – это метод, связанный с классом, а не с экземпляром класса; он вызывается через сам класс, а не через конкретный экземпляр класса. Метод _Date.parse\(\)_ – это метод класса. Он всегда вызывается через объект конструктора _Date_, а не через конкретный экземпляр класса _Date_.

Поскольку методы класса вызываются через функцию-конструктор, они не могут использовать ключевое слово this для ссылки на какой-либо конкретный экземпляр класса, поскольку в данном случае this ссылается на саму функцию-конструктор. \(Обычно ключевое слово this в методах классов вообще не используется.\)

Как и свойства класса, методы класса являются глобальными. Методы класса не работают с конкретным экземпляром, поэтому их, как правило, проще рассматривать в качестве функций, вызываемых через класс. Как и в случае со свойствами класса, связь этих функций с классом дает им в пространстве имен JavaScript удобную нишу и предотвращает возникновение конфликтов имен. Для того, чтобы определить метод класса в JavaScript, требуется сделать соответствующую функцию свойством конструктора.

## Стандартные встроенные объекты

В JavaScript есть несколько объектов, встроенных в ядро, например[`Math`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Math),[`Object`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Object),[`Array`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Array) и[`String`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/String). Пример ниже показывает, как использовать объект Math, чтобы получить случайное число, используя его метод random\(\).

```javascript
console.log(Math.random());
```

Каждый объект в JavaScript является экземпляром объекта [`Object`](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Object), следовательно наследует все его свойства и методы \(исключение – результат вызова Object.create\(null\)\).

