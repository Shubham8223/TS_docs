# Object-Oriented Programming (OOP) Concepts

## Introduction
Object-Oriented Programming (OOP) is a programming paradigm based on the concept of objects, which can contain data and methods to operate on that data. OOP helps in structuring complex programs, promoting code reusability, and improving maintainability.

---

## 1. Core OOP Concepts

### 1.1 Class & Object
A **class** is a blueprint for creating objects. An **object** is an instance of a class.

#### Example in TypeScript:
```ts
class Car {
  brand: string;
  constructor(brand: string) {
    this.brand = brand;
  }
  drive() {
    console.log(`${this.brand} is driving!`);
  }
}

const myCar = new Car("Tesla");
myCar.drive();
```

---

### 1.2 Encapsulation
Encapsulation is the mechanism of restricting direct access to some components of an object.

#### Example:
```ts
class BankAccount {
  private balance: number;
  constructor(initialBalance: number) {
    this.balance = initialBalance;
  }
  deposit(amount: number) {
    this.balance += amount;
  }
  getBalance(): number {
    return this.balance;
  }
}
const account = new BankAccount(1000);
account.deposit(500);
console.log(account.getBalance()); // 1500
```

---

### 1.3 Inheritance
Inheritance allows a class to inherit properties and methods from another class.

#### Example:
```ts
class Animal {
  constructor(public name: string) {}
  makeSound() {
    console.log("Some generic sound");
  }
}
class Dog extends Animal {
  makeSound() {
    console.log("Bark!");
  }
}
const dog = new Dog("Buddy");
dog.makeSound();
```

---

### 1.4 Polymorphism
Polymorphism allows a method to have different implementations depending on the object that calls it.

#### Example:
```ts
class Shape {
  area(): number {
    return 0;
  }
}
class Circle extends Shape {
  constructor(private radius: number) {
    super();
  }
  area(): number {
    return Math.PI * this.radius * this.radius;
  }
}
const myCircle = new Circle(5);
console.log(myCircle.area());
```

---

### 1.5 Abstraction
Abstraction hides implementation details and exposes only the essential features.

#### Example:
```ts
abstract class Vehicle {
  constructor(protected speed: number) {}
  abstract move(): void;
}
class Car extends Vehicle {
  move() {
    console.log(`The car moves at ${this.speed} km/h`);
  }
}
const myCar = new Car(120);
myCar.move();
```

---

## 2. OOP Principles in TypeScript

### 2.1 Getters and Setters
```ts
class Person {
  private _age: number;
  constructor(age: number) {
    this._age = age;
  }
  get age(): number {
    return this._age;
  }
  set age(newAge: number) {
    if (newAge > 0) this._age = newAge;
    else throw new Error("Age must be positive");
  }
}
const person = new Person(30);
person.age = 35;
console.log(person.age);
```

---

### 2.2 Static Properties and Methods
Static properties and methods belong to the class rather than an instance.
```ts
class MathUtil {
  static PI = 3.14;
  static circleArea(radius: number): number {
    return this.PI * radius * radius;
  }
}
console.log(MathUtil.circleArea(5));
```

---

### 2.3 Interfaces and Implementation
Interfaces define a contract that a class must follow.
```ts
interface IShape {
  area(): number;
}
class Square implements IShape {
  constructor(private side: number) {}
  area(): number {
    return this.side * this.side;
  }
}
const square = new Square(4);
console.log(square.area());
```

---

### 2.4 Dependency Injection
Dependency Injection helps decouple classes and makes code more maintainable.
```ts
class Engine {
  start() {
    console.log("Engine started");
  }
}
class Car {
  constructor(private engine: Engine) {}
  start() {
    this.engine.start();
  }
}
const engine = new Engine();
const myCar = new Car(engine);
myCar.start();
```

---

## 3. Design Patterns in OOP

### 3.1 Singleton Pattern
Ensures only one instance of a class exists.
```ts
class Singleton {
  private static instance: Singleton;
  private constructor() {}
  static getInstance(): Singleton {
    if (!this.instance) {
      this.instance = new Singleton();
    }
    return this.instance;
  }
}
const singleInstance = Singleton.getInstance();
```

### 3.2 Factory Pattern
Creates objects without specifying the exact class.
```ts
class Car {
  constructor(public brand: string) {}
}
class CarFactory {
  static createCar(brand: string): Car {
    return new Car(brand);
  }
}
const myCar = CarFactory.createCar("Toyota");
```

### 3.3 Observer Pattern
Allows objects to be notified of state changes.
```ts
class Observer {
  update(message: string) {
    console.log("Received message:", message);
  }
}
class Subject {
  private observers: Observer[] = [];
  addObserver(observer: Observer) {
    this.observers.push(observer);
  }
  notifyObservers(message: string) {
    this.observers.forEach((obs) => obs.update(message));
  }
}
const observer1 = new Observer();
const subject = new Subject();
subject.addObserver(observer1);
subject.notifyObservers("Hello Observers");
```

---

## Conclusion
OOP provides a structured way to build scalable applications by encapsulating data, promoting code reusability, and following best design principles. Mastering these concepts enhances software development efficiency and maintainability.

