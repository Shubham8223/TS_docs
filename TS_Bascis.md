# TypeScript Complete Guide

## Introduction
TypeScript is a strongly typed superset of JavaScript that compiles to plain JavaScript. It provides static typing, interfaces, generics, and advanced features to improve code quality and maintainability.

---

## 1. TypeScript Basics

### Variables & Types
```ts
let age: number = 25;
let name: string = "Shubham";
let isDeveloper: boolean = true;
let skills: string[] = ["JavaScript", "TypeScript", "React"];
let user: { name: string; age: number } = { name: "Shubham", age: 25 };
```

### Functions
```ts
function greet(name: string): string {
  return `Hello, ${name}!`;
}
```

### Interfaces
```ts
interface User {
  name: string;
  age: number;
}

const user1: User = { name: "Shubham", age: 25 };
```

### Classes
```ts
class Person {
  constructor(public name: string, private age: number) {}

  getAge(): number {
    return this.age;
  }
}
```

### Generics
```ts
function identity<T>(value: T): T {
  return value;
}
const output = identity<number>(10);
```

---

## 2. Advanced TypeScript Features

### Utility Types
#### `Partial<T>` (Makes properties optional)
```ts
interface User {
  name: string;
  age: number;
}
const updateUser = (user: Partial<User>) => {
  console.log(user);
};
updateUser({ name: "Shubham" });
```

#### `Readonly<T>` (Makes properties read-only)
```ts
const user: Readonly<User> = { name: "Shubham", age: 25 };
// user.age = 26; // ❌ Error: Cannot assign to 'age' because it is a read-only property.
```

#### `Pick<T, K>` (Extracts specific properties)
```ts
type UserName = Pick<User, "name">;
```

#### `Omit<T, K>` (Removes specific properties)
```ts
type UserWithoutAge = Omit<User, "age">;
```

#### `Record<K, T>` (Creates an object type with specified keys)
```ts
type Roles = "admin" | "user" | "guest";
const userRoles: Record<Roles, boolean> = {
  admin: true,
  user: false,
  guest: false,
};
```

---

## 3. Decorators in TypeScript

### Enabling Decorators
Enable decorators in `tsconfig.json`:
```json
{
  "compilerOptions": {
    "experimentalDecorators": true,
    "emitDecoratorMetadata": true
  }
}
```

### Class Decorator
```ts
function Logger(constructor: Function) {
  console.log(`Class ${constructor.name} is created`);
}

@Logger
class Person {
  constructor(public name: string) {}
}
```

### Method Decorator
```ts
function LogMethod(target: any, methodName: string, descriptor: PropertyDescriptor) {
  const originalMethod = descriptor.value;
  descriptor.value = function (...args: any[]) {
    console.log(`Calling ${methodName} with args:`, args);
    return originalMethod.apply(this, args);
  };
}

class MathOperations {
  @LogMethod
  multiply(a: number, b: number) {
    return a * b;
  }
}
```

### Property Decorator
```ts
function MinLength(len: number) {
  return function (target: any, propertyKey: string) {
    let value: string;

    Object.defineProperty(target, propertyKey, {
      get: () => value,
      set: (newValue: string) => {
        if (newValue.length < len) {
          throw new Error(`Length of ${propertyKey} should be at least ${len} characters.`);
        }
        value = newValue;
      },
    });
  };
}
```

---

## 4. `bind()` in TypeScript

### Fixing `this` issues in JavaScript
```ts
class Button {
  text = "Click me";
  click() {
    console.log(this.text);
  }
}
const btn = new Button();
const clickFunc = btn.click.bind(btn);
clickFunc();
```

---

## 5. Commonly Used Utility Functions

### Debounce Function (Optimize API Calls)
```ts
function debounce<T extends (...args: any[]) => void>(func: T, delay: number): T {
  let timer: NodeJS.Timeout;
  return ((...args: any[]) => {
    clearTimeout(timer);
    timer = setTimeout(() => func(...args), delay);
  }) as T;
}
```

### Throttle Function (Limit API Calls)
```ts
function throttle<T extends (...args: any[]) => void>(func: T, limit: number): T {
  let lastCall = 0;
  return ((...args: any[]) => {
    const now = Date.now();
    if (now - lastCall >= limit) {
      lastCall = now;
      func(...args);
    }
  }) as T;
}
```

### Deep Clone an Object
```ts
function deepClone<T>(obj: T): T {
  return JSON.parse(JSON.stringify(obj));
}
```

---

## 6. Advanced TypeScript Topics

### Conditional Types
```ts
type IsString<T> = T extends string ? "Yes" : "No";
type Test1 = IsString<string>; // "Yes"
type Test2 = IsString<number>; // "No"
```

### Mapped Types
```ts
type Optional<T> = { [K in keyof T]?: T[K] };
type UserOptional = Optional<User>;
```

### Template Literal Types
```ts
type Greeting = `Hello, ${string}`;
const greet: Greeting = "Hello, Shubham";
```

---


