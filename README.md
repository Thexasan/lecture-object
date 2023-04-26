# lecture-object
# Что такое Object in JS?
> Object в JavaScript - это сборный тип данных, который может содержать свойства и методы. Он является одним из базовых типов данных в JavaScript и используется для хранения объектов в программах на этом языке.

> Объекты в JS представлены в виде пар ключ-значение. Ключем является имя свойства или метода, а значением может быть любое значение включая другой объект.  Чтобы создать объект в JavaScript, можно использовать фигурные скобки `{}`:

```js
let person = {
  name: "John",
  age: 30,
  isAdmin: true
};
```

> В этом примере мы создали объект `person`, который содержит три свойства: `name`, `age` и `isAdmin`. У каждого свойства есть свое имя и значение.

* Можно обратиться к каждому свойству объекта через оператор точки `.`:

``` js
console.log(person.name); // "John"
console.log(person.age); // 30
console.log(person.isAdmin); // true
```

* Также можно добавлять новые свойства и методы в объект:

```js
person.lastName = "Doe";
person.getFullName = function() {
  return this.name + " " + this.lastName;
};

console.log(person.getFullName()); // "John Doe"
```

> В этом примере мы добавили новое свойство `lastName` и новый метод `getFullName()`, который возвращает полное имя объекта `person`.

> Object в JavaScript очень мощный тип данных, который используется в программировании на этом языке для создания сложных структур данных и объектов, а также для работы с многими библиотеками и фреймворками.

# Methods Object
> Object в JavaScript имеет множество методов, которые позволяют работать с объектами, свойствами и методами. Некоторые из наиболее используемых методов Object:

## 1. `Object.keys(obj)` - возвращает массив имен свойств объекта `obj`.

```js
let person = {
  name: "John",
  age: 30,
  isAdmin: true
};

console.log(Object.keys(person)); // [ "name", "age", "isAdmin" ]
```

## 2. `Object.values(obj)` - возвращает массив значений свойств объекта `obj`.

```js
let person = {
  name: "John",
  age: 30,
  isAdmin: true
};

console.log(Object.values(person)); // [ "John", 30, true ]
```

## 3. `Object.entries(obj)` - возвращает массив `[key, value]` для каждого свойства объекта `obj`.

```js
let person = {
  name: "John",
  age: 30,
  isAdmin: true
};

console.log(Object.entries(person)); // [ ["name", "John"], ["age", 30], ["isAdmin", true] ]
```

## 4. `Object.assign(target, ...sources)` - копирует значения всех перечисляемых свойств из одного или нескольких исходных объектов `...sources` в целевой объект `target`. Возвращает объект `target`.

```js
let obj1 = { a: 1, b: 2 };
let obj2 = { c: 3, d: 4 };
let mergedObj = Object.assign(obj1, obj2);

console.log(mergedObj); // { a: 1, b: 2, c: 3, d: 4 }
```

## 5. `Object.create(proto, [propertiesObject])` - создает новый объект с указанным прототипом `proto` и необязательными дескрипторами свойств из `propertiesObject`.

```js
let person = {
  name: "John",
  age: 30,
  isAdmin: true
};
let student = Object.create(person, { 
  name: { value: "Alice" },
  age: { value: 21 },
  isAdmin: { value: false }
});

console.log(student.name); // "Alice"
console.log(student.age); // 21
console.log(student.isAdmin); // false
```

> Это только некоторые методы, которые можно использовать с объектами в JavaScript. Object имеет множество других методов, которые позволяют работать с объектами, массивами, функциями и т.д.

# What is Desructuring and Spread in js?
> Destructuring и spread - это две функции, которые используются для работы с объектами и массивами в JavaScript.

> Destructuring (деструктуризация) позволяет извлечь значения свойств объекта или элементов массива в отдельные переменные. Вот примеры:

## 1. Деструктуризация объекта:

```js
let person = {name: "John", age: 30};
let {name, age} = person;

console.log(name); // "John"
console.log(age); // 30
```

## 2. Деструктуризация массива:

```js
let numbers = [1, 2, 3, 4];
let [a, b, ...rest] = numbers;

console.log(a); // 1
console.log(b); // 2
console.log(rest); // [3, 4]
```

* В этом примере мы используем оператор `...` для присвоения оставшихся элементов массива в переменную `rest`.

> Spread (распространение) позволяет объединять несколько объектов или массивов в один. Например:

## 1. Распространение объектов:

```js
let person = {name: "John", age: 30};
let job = {title: "Developer", salary: 5000};

let employee = {...person, ...job};

console.log(employee); // { name: "John", age: 30, title: "Developer", salary: 5000 }
```

## 2. Распространение массивов:

```js
let numbers = [1, 2];
let moreNumbers = [3, 4];

let allNumbers = [...numbers, ...moreNumbers];

console.log(allNumbers); // [1, 2, 3, 4]
```

> Spread можно использовать для объединения массивов или объектов вместе. Он также может использоваться для создания копии массива или объекта без изменения оригинала.

> Destructuring и spread - это две мощные функции в JavaScript, которые позволяют более эффективно работать с объектами и массивами.

# What is keyword "this" in JS?
> `this` - это специальное ключевое слово в JavaScript, которое ссылается на объект, в контексте которого вызывается текущая функция. `this` всегда ссылается на объект, который является "владельцем" кода, который сейчас выполняется.

> Контекст `this` может быть разным в зависимости от того, как функция была вызвана. Рассмотрим некоторые примеры.

## 1. Контекст `this` в обычной функции:

```js
function sayName() {
  console.log(this.name);
}

let person = {
  name: "John",
  sayName: sayName
};

person.sayName(); // "John"
```

> В этом примере мы создали функцию `sayName()`, которая выводит имя объекта `this`. Мы создали объект `person`, который содержит свойство `name` и метод `sayName()`, который ссылается на функцию `sayName()`. Когда мы вызываем метод `sayName()` на объекте `person`, выполнение кода переносится в контекст объекта `person`, поэтому `this` внутри `sayName()` ссылается на объект `person`, а не на глобальный объект.

## 2. Контекст `this` при использовании стрелочной функции:

```js
let person = {
  name: "John",
  sayName: () => {
    console.log(this.name);
  }
};

person.sayName(); // undefined
```

> В этом примере мы используем стрелочную функцию для метода объекта `person`. Контекст `this` внутри стрелочной функции не изменяется, поэтому `this` ссылается на глобальный объект.

## 3. Контекст `this` в функции-конструкторе:

```js
function Person(name) {
  this.name = name;
}

let john = new Person("John");
console.log(john.name); // "John"
```

> В этом примере мы создали функцию-конструктор `Person()`, которая устанавливает свойство `name` для объекта, создаваемого с помощью оператора `new`. Когда мы создаем объект `john`, `this` внутри `Person()` ссылается на объект, создаваемый оператором `new`.

* `this` - это очень важное понятие в JavaScript и его контекст может сильно влиять на работу программы, поэтому важно понимать, как он работает.

# What is new data() in JS?
> `new Date()` в JavaScript создает новый объект типа `Date`. Этот объект представляет собой дату и время, которые можно использовать для выполнения различных операций с датами в JavaScript.

> Если вызвать конструктор `new Date()` без параметров, то созданный объект будет представлять текущую дату и время на момент создания. Однако можно передать параметры в конструктор для создания объекта, представляющего определенную дату и время.

> Например, чтобы создать объект типа `Date` для определенной даты, можно передать три параметра: год, месяц (от 0 до 11) и день:

```js
var specificDate = new Date(2022, 1, 1);
```

* Эта строка создаст объект `specificDate`, представляющий 1 февраля 2022 года.

> Также можно передать более чем три параметра, чтобы указать еще и время:

```js
var specificDateAndTime = new Date(2022, 1, 1, 12, 30, 0);
```

*Эта строка создаст объект `specificDateAndTime`, представляющий 1 февраля 2022 года, 12:30.

> Объект `Date` имеет множество методов и свойств для работы с датами и временем, например, `getDate()`, `getMonth()`, `getFullYear()`, `getHours()`, `getMinutes()`, `getSeconds()`, `getTime()`, `setDate()`, `setMonth()`, `setFullYear()` и т.д.

# Creating date ojects.
> There are four ways to create a date object.
* 1. new Date()
* 2. new Date(milliseconds)
* 3. new Date(Date string)
* 4. new Date(year,month,day,hours,minutes,seconds,milliseconds)

# DAta and time
> Методы new Date() в JavaScript используются для создания объекта даты. Они выполняют роль в работе с датами и временем, позволяя получать, устанавливать и манипулировать различными значениями даты и времени.

## Примеры методов new Date():

### 1. new Date() - создает объект даты, содержащий текущую дату и время.

```js
const currentDate = new Date();
console.log(currentDate); // выводит текущую дату и время
```

### 2. new Date(milliseconds) - создает объект даты, содержащий дату и время, соответствующие заданному количеству миллисекунд, прошедших с начала эпохи Unix (1 января 1970 года).

```js
const dateFromMilliseconds = new Date(1616582400000);
console.log(dateFromMilliseconds); // выводит дату, соответствующую заданному количеству миллисекунд
```

### 3. new Date(dateString) - создает объект даты, содержащий дату и время, соответствующие заданной строке даты. Строка должна быть в формате, который может быть распознан методом Date.parse().

```js
const dateFromString = new Date('2021-03-24T10:00:00Z');
console.log(dateFromString); // выводит дату, соответствующую заданной строке даты
```

### 4. new Date(year, month, day, hours, minutes, seconds, milliseconds) - создает объект даты, содержащий заданную дату и время.

```js
const customDate = new Date(2021, 2, 24, 10, 0, 0, 0);
console.log(customDate); // выводит заданную дату и время
```

### 5. date.getFullYear() - возвращает год объекта даты.

```js
const currentDate = new Date();
console.log(currentDate.getFullYear()); // выводит текущий год
```

### 6. date.getMonth() - возвращает месяц объекта даты (от 0 до 11, где 0 - январь, 11 - декабрь).

```js
const currentDate = new Date();
console.log(currentDate.getMonth()); // выводит текущий месяц
```

### 7. date.getDate() - возвращает день месяца объекта даты (от 1 до 31).

```js
const currentDate = new Date();
console.log(currentDate.getDate()); // выводит текущий день месяца
```

### 8. date.getHours() - возвращает час объекта даты (от 0 до 23).

```js
const currentDate = new Date();
console.log(currentDate.getHours()); // выводит текущий час
```

### 9. date.getMinutes() - возвращает минуты объекта даты (от 0 до 59).

```js
const currentDate = new Date();
console.log(currentDate.getMinutes()); // выводит текущие минуты
```

### 10. date.getSeconds() - возвращает секунды объекта даты (от 0 до 59).

```js
const currentDate = new Date();
console.log(currentDate.getSeconds()); // выводит текущие секунды
```