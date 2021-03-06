# Шаблоны проектирования

[Шаблон проектирования](https://ru.wikipedia.org/wiki/%D0%A8%D0%B0%D0%B1%D0%BB%D0%BE%D0%BD_%D0%BF%D1%80%D0%BE%D0%B5%D0%BA%D1%82%D0%B8%D1%80%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D1%8F)

[Паттерны проектирования в JavaScript](https://habr.com/ru/company/ruvds/blog/427293/)

[Learning JavaScript Design Patterns](https://addyosmani.com/resources/essentialjsdesignpatterns/book/)

## Что такое паттерн?

- Повторяемое решение которое может применяться к часто возникающим проблемам дизайна софта (JavaScript приложений)
- Можно воспринимать как лекала (шаблон) программирования
- Могут применяться в разных ситуациях

Очень широкая тема.

## Преимущества использования паттернов

- Это проверенное решения: Они предлагают надежные решения для решения проблем программной разработки используя проверенные техники которые отражают опыт и знания разработчиков, которые помогли их решить и внести в паттерн.
- Паттерны могут быть использованы повторно: Обычно шаблон отражает готовое решение, которое можно адаптировать к нашим собственным потребностям.
- Шаблоны могут быть выразительными: когда мы смотрим на шаблон, то, как правило, есть структура решения и термины представленного решения, которые могут помочь выразить довольно большие решения очень элегантно.

## Какие паттерны мы посмотрим?

- Module
- Revealing module
- Singleton
- Factory
- Observer
- Mediator
- State

## Module & Revealing Module Pattern

Тема про ES2015 модули

[Освоение шаблона Модуль](https://toddmotto.com/mastering-the-module-pattern/)
[YDKJS про модули](https://github.com/getify/You-Dont-Know-JS/blob/master/scope%20&%20closures/ch5.md#modules)

Позволяет разбивать код на самостоятельные модули с приватными переменными и функциями.

```javascript
var myRevealingModule = (function() {
  var privateCounter = 0;

  function privateFunction() {
    privateCounter++;
  }

  function publicFunction() {
    publicIncrement();
  }

  function publicIncrement() {
    privateFunction();
  }

  function publicGetCount() {
    return privateCounter;
  }

  // Reveal public pointers to
  // private functions and properties

  return {
    start: publicFunction,
    increment: publicIncrement,
    count: publicGetCount
  };
})();

myRevealingModule.start();
myRevealingModule.increment();
myRevealingModule.count(); //?
```

## Singleton Одиночка

Это IIFE которая возвращает один единственный объект каждый раз. Повторные вызовы конструктора будут возвращать все тот же единственный объект.

Отличаются от классов или объектов тем, что мы можем отложить их инициализацию, в основном, потому что они могут требовать некоторую информацию которая еще не доступна в момент запуска программы.

[Singleton](https://addyosmani.com/resources/essentialjsdesignpatterns/book/#singletonpatternjavascript)

```javascript
const Singleton = (function() {
  let instance;

  function createInstance() {
    const object = new Object("Object Instance!!!");
    return object;
  }
  return {
    getInstance: function() {
      if (!instance) {
        instance = createInstance();
      }
      return instance;
    }
  };
})();

const instanceA = Singleton.getInstance();
const instanceB = Singleton.getInstance();
console.log(instanceA);
console.log(instanceB);

console.log(instanceA === instanceB);
```

## Factory Фабрика

Позволяет создавать объекты, в отличие от конструктора, может создавать объекты различных классов, в зависимости от внутренней логики и параметров которые мы ему передаем.

Часто используется в приложениях где нужно управлять объектами разных типов, которые разделяют множество общих свойств.

[Factory](https://addyosmani.com/resources/essentialjsdesignpatterns/book/#factorypatternjavascript)

Фабрика типов участников

```javascript
function MemberFactory() {
  this.createMember = function(name, type) {
    let member;
    // simple, standard, super
    if (type === "simple") {
      member = new SimpleMembership(name);
    } else if (type === "standard") {
      member = new StandardMembership(name);
    } else if (type === "super") {
      member = new SuperMembership(name);
    }

    member.type = type;

    member.define = function() {
      console.log(`${this.name} (${this.type}): ${this.cost}`);
    };
    return member;
  };
}

const SimpleMembership = function(name) {
  this.name = name;
  this.cost = "$5";
};

const StandardMembership = function(name) {
  this.name = name;
  this.cost = "$15";
};

const SuperMembership = function(name) {
  this.name = name;
  this.cost = "$25";
};

const members = [];
const factory = new MemberFactory();

members.push(factory.createMember("John Doe", "simple"));
members.push(factory.createMember("Jennis Williams", "super"));
members.push(factory.createMember("Tom Smith", "super"));

// console.log(members);

members.forEach(member => {
  member.define();
});
```

## Observer Наблюдатель

[The Observer Pattern](https://addyosmani.com/resources/essentialjsdesignpatterns/book/#observerpatternjavascript)

[Refactoring.guru Observer](https://refactoring.guru/ru/design-patterns/observer)

Позволяет подписываться/отписываться на какие-то события/функциональность. Можно использовать для уведомления DOM что какой-то элемент обновился.

Создадим кнопки для подписки/отписки на события

Переделаем на ES2015

## Mediator

[Mediator](https://addyosmani.com/resources/essentialjsdesignpatterns/book/#mediatorpatternjavascript)

[Refactoring.guru Mediator](https://refactoring.guru/ru/design-patterns/mediator)

Паттерн Медиатор используется для централизаци сложных взаимодействий и управления между связанными объектами.

- Объекты системы говорят Медиатору, что их состояние изменилось.
- Объекты отвечают на запросы из Медиатора.

Перед тем как добавить Медиатор в систему, все объекты должны были знать друг о друге и знать как взаимодействовать между собой напрямую... Они были тесно связаны. С Медиатором объекты полностью не связаны между собой (общаются с Медиатором).

Медиатор содержит всю управляющую логику всей системы. Когда существующее приложение нуждается в новых правилах или новы объект добавляется в систему, вам будет понятно, что всю необходимую логику нужно добавить в медиатор (а не в каждый из заинтересованных в новшестве объект).

Поведенческий паттерн который позволяет выставить унифицированный интерфейс с помощью которого будут взаимодействовать различные части системы.

Если кажется, что система имеет слишком много прямых связей между компонентами, возможно пришло время создать центральную точку управления, через которую будут взаимодействовать компоненты. Медиатор предлагает слабое связывание обеспечивая взаимодействие компонентов не явно между собой, их взаимодействие происходит через эту центральную точку.

![Без медиатора](/articles/2019.03.04-patterns/01-no-mediator.png)
![С медиатором](/articles/2019.03.04-patterns/02-mediator.png)

Аналогией из реального мира может быть система управления движением в аэропорту (авиадиспетчер). Башня (медиатор) определяет какие самолеты могут взлететь и приземлиться, потому что все взаимодействия (сообщения переданы или приняты) сделаны между самолетом и башней, а не напрямую между самолетами. Централизованный контроллер это ключ к успеху в таких системах и это та роль которую играет паттерн Медиатор в дизайне программ.

[Pen Meidator](https://codepen.io/curtdp/pen/qvRXVr?editors=0012)

## State Состояние

Нормальный пример [State](https://www.dofactory.com/javascript/state-design-pattern)
