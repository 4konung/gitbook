## Объекты, создаваемые пользователем

#### Класс {#The_Class}

JavaScript — это прототипно-ориентированный язык, и в нём нет оператора`class`, который имеет место в C++ или Java. Иногда это сбивает с толку программистов, привыкших к языкам с оператором`class`. Вместо этого JavaScript использует функции как конструкторы классов \(В es6 появилось ключевое слово _class,_ для упрощение описания конструкторов\). Объявить класс так же просто как объявить функцию. В примере ниже мы объявляем новый класс Person с пустым конструктором:

```js
var Person = function () {};
```

#### Объект \(экземпляр класса\) {#The_Object_.28Class_Instance.29}

Для создания нового экзмепляра объекта `obj`мы используем оператор `new obj`, присваивая результат \(который имеет тип`obj`\) в переменную.

В примере выше мы определили класс`Person`. В примере ниже мы создаём два его экземпляра \(`person1`и`person2`\).

```js
var person1 = new Person();
var person2 = new Person();
```

#### Конструктор {#The_Constructor}

Конструктор вызывается в момент создания экземпляра класса \(в тот самый момент, когда создается объект\). Конструктор является методом класса. В JavaScript функция служит конструктором объекта, поэтому нет необходимости явно определять метод конструктор. Любое действие определенное в классе будет выполненно в момент создания экземпляра класса.

Конструктор используется для задания свойств объекта или для вызова методов, которые подготовят объект к использованию. Добавление методов и их описаний производится с использованием другого синтаксиса, описанного далее в этой статье.

В примере ниже, конструктор класса `Person` выводит в консоль сообщение в момент создания нового экземпляра `Person`.

```js
var Person = function () {
  console.log('instance created');
};

var person1 = new Person();
var person2 = new Person();
```

#### Свойство \(аттрибут объекта\) {#The_Property_.28object_attribute.29}

Свойства — это переменные, содержащиеся в классе; каждый экземпляр объекта имеет эти свойства. Свойства устанавливаются в конструкторе \(функции\) класса, таким образом они создаются для каждого экземпляра.

Ключевое слово`this`, которое ссылается на текущий объект, позволяет вам работать со свойствами класса. Доступ \(чтение и запись\) к свойствам снаружи класса осуществляется синтаксисом `InstanceName.Property,` так же как в C++, Java и некоторых других языках. \(Внутри класса для получения и изменения значений свойств используется синтаксис`this.Property`\)

В примере ниже, мы определяем свойство `firstName`для класса `Person`при создании экземпляра:

```js
var Person = function (firstName) {
  this.firstName = firstName;
  console.log('Person instantiated');
};

var person1 = new Person('Alice');
var person2 = new Person('Bob');

// Выводит свойство firstName в консоль
console.log('person1 is ' + person1.firstName); // выведет "person1 is Alice"
console.log('person2 is ' + person2.firstName); // выведет "person2 is Bob"
```

#### Методы {#The_methods}

Методы — это функции \(и определяются как функции\), но с другой стороны следуют той же логике, что и свойства. Вызов метода похож на доступ к свойству, но вы добавляете \(\) на конце имени метода, возможно, с аргументами. Чтобы объявить метод, присвойте функцию в именованное свойство свойства`prototype` класса. Потом вы сможете вызвать метод объекта под тем именем, которое вы присвоили функции.

В примере ниже мы определяем и используем метод`sayHello()`для класса`Person`.

```js
var Person = function (firstName) {
  this.firstName = firstName;
};

Person.prototype.sayHello = function() {
  console.log("Hello, I'm " + this.firstName);
};

var person1 = new Person("Alice");
var person2 = new Person("Bob");

// вызываем метод sayHello() класса Person
person1.sayHello(); // выведет "Hello, I'm Alice"
person2.sayHello(); // выведет "Hello, I'm Bob"
```

В JavaScript методы это — обычные объекты функций, связанные с объектом как свойства: это означает, что вы можете вызывать методы "вне контекста". Рассмотрим следующий пример:

```js
var Person = function (firstName) {
  this.firstName = firstName;
};

Person.prototype.sayHello = function() {
  console.log("Hello, I'm " + this.firstName);
};

var person1 = new Person("Alice");
var person2 = new Person("Bob");
var helloFunction = person1.sayHello;

// выведет "Hello, I'm Alice"
person1.sayHello();

// выведет "Hello, I'm Bob"
person2.sayHello();

// выведет "Hello, I'm undefined" (or fails
// with a TypeError in strict mode)
helloFunction();                                    

// выведет true
console.log(helloFunction === person1.sayHello);

// выведет true
console.log(helloFunction === Person.prototype.sayHello);

// выведет "Hello, I'm Alice"
helloFunction.call(person1);
```

Как показывает пример, все ссылки, которые мы имеем на функцию `sayHello`— `person1`,`Person.prototype`, переменная`helloFunction` и т.д. — ссылаются на одну и ту же функцию. Значение`this`в момент вызова функции зависит от того, как мы её вызываем. Наиболее часто мы обращаемся к`this`в выражениях, где мы получаем функцию из свойства объекта —`person1.sayHello()` —`this` устанавливается на объект, из которого мы получили функцию \(`person1`\), вот почему`person1.sayHello()` использует имя "Alice", а`person2.sayHello()`использует имя "Bob". Но если вызов будет совершён иначе, то`this`будет иным: вызов`this`из переменной —`helloFunction()`— установит`this`на глобальный объект \(`window`в браузерах\). Так как этот объект \(вероятно\) не имеет свойства`firstName`, функция выведет "Hello, I'm undefined" \(так произойдёт в нестрогом режиме; в[strict mode](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Strict_mode)всё будет иначе \(ошибка\), не будем сейчас вдаваться в подробности, чтобы избежать путаницы\). Или мы можем указать`this`явно с помощью`Function#call`\(или`Function#apply`\) как показано в конце примера.

#### Наследование {#Inheritance}

Наследование — это способ создать класс как специализированную версию одного или нескольких классов \(JavaScript поддерживает только одиночное наследование\). Специализированный класс, как правило, называют потомком, а другой класс родителем. В JavaScript наследование осуществляется присвоением экземпляра класса родителя классу потомку. В современных браузерах вы можете реализовать наследование с помощью [Object.create](https://developer.mozilla.org/ru/docs/Web/JavaScript/Reference/Global_Objects/Object/create#Classical_inheritance_with_Object.create).

В примере ниже мы определяем класс`Student`как потомка класса`Person`. Потом мы переопределяем метод`sayHello()`и добавляем метод`addGoodBye()`

```js
// Определяем конструктор Person
var Person = function(firstName) {
  this.firstName = firstName;
};

// Добавляем пару методов в Person.prototype
Person.prototype.walk = function(){
  console.log("I am walking!");
};

Person.prototype.sayHello = function(){
  console.log("Hello, I'm " + this.firstName);
};

// Определяем конструктор Student
function Student(firstName, subject) {
  // Вызываем конструктор родителя, убедившись (используя Function#call)
  // что "this" в момент вызова установлен корректно
  Person.call(this, firstName);

  // Инициируем свойства класса Student
  this.subject = subject;
};

// Создаём объект Student.prototype, который наследуется от Person.prototype.
// Примечание: Рспространённая ошибка здесь, это использование "new Person()", чтобы создать
// Student.prototype. Это неверно по нескольким причинам, не в последнюю очередь
// потому, что нам нечего передать в Person в качестве аргумента "firstName"
// Правильное место для вызова Person показано выше, где мы вызываем 
// его в конструкторе Student.
Student.prototype = Object.create(Person.prototype); // Смотрите примечание выше

// Устанавливаем свойство "constructor" для ссылки на класс Student
Student.prototype.constructor = Student;

// Заменяем метод "sayHello"
Student.prototype.sayHello = function(){
  console.log("Hello, I'm " + this.firstName + ". I'm studying "
              + this.subject + ".");
};

// Добавляем метод "sayGoodBye"
Student.prototype.sayGoodBye = function(){
  console.log("Goodbye!");
};

// Пример использования:
var student1 = new Student("Janet", "Applied Physics");
student1.sayHello();   // "Hello, I'm Janet. I'm studying Applied Physics."
student1.walk();       // "I am walking!"
student1.sayGoodBye(); // "Goodbye!"

// Проверяем, что instanceof работает корректно
console.log(student1 instanceof Person);  // true 
console.log(student1 instanceof Student); // true
```

Относительно строки `Student.prototype = Object.create(Person.prototype);`: В старых движках JavaScript, в которых нет  [`Object.create`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/create) можно использовать полифилл \(ещё известный как "shim"\) или функцию которая достигает тех же результатов, такую как:

```js
function createObject(proto) {
    function ctor() { }
    ctor.prototype = proto;
    return new ctor();
}

// Пример использования:
Student.prototype = createObject(Person.prototype);
```

#### Инкапсуляция {#Encapsulation}

В примере выше классу `Student` нет необходимости знать о реализации метода`walk()` класса`Person`, но он может его использовать; Класс`Student` не должен явно определять этот метод, пока мы не хотим его изменить. Это называется **инкапсуляция**, благодаря чему каждый класс собирает данные и методы в одном блоке.

Сокрытие информации распространённая особенность, часто реализуемая в других языках программирования как приватные и защищённые методы/свойства. Однако в JavaScript можно лишь имитировать нечто подобное, это не является необходимым требованием объектно-ориентированного программирования.

#### Полиморфизм {#Polymorphism}

Так как все методы и свойства определяются внутри свойства`prototype`, различные классы могут определять методы с одинаковыми именами; методы находятся в области видимости класса в котором они определены, пока два класса не имеют связи родитель-потомок \(например, один наследуется от другого в цепочке наследований\).

