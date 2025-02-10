# TypeScript Utility Methods Documentation

## **1. Loops in TypeScript**

### **1.1 For Loop**
The `for` loop executes a block of code a specified number of times.
```ts
for (let i: number = 0; i < 5; i++) {
  console.log(i);
}
```

### **1.2 While Loop**
The `while` loop executes as long as the condition is `true`.
```ts
let count: number = 0;
while (count < 5) {
  console.log(count);
  count++;
}
```

### **1.3 Do-While Loop**
Executes at least once before checking the condition.
```ts
let num: number = 0;
do {
  console.log(num);
  num++;
} while (num < 5);
```

### **1.4 For...of Loop**
Iterates over an array or iterable.
```ts
const numbers: number[] = [10, 20, 30];
for (const num of numbers) {
  console.log(num);
}
```

### **1.5 For...in Loop**
Iterates over object properties.
```ts
const user: { name: string; age: number } = { name: "Alice", age: 25 };
for (const key in user) {
  console.log(`${key}: ${user[key as keyof typeof user]}`);
}
```

---

## **2. Array Methods in TypeScript**

### **2.1 map()**
Creates a new array by applying a function to each element.
```ts
const numbers: number[] = [1, 2, 3];
const doubled: number[] = numbers.map((num: number) => num * 2);
console.log(doubled); // [2, 4, 6]
```

### **2.2 filter()**
Filters elements based on a condition.
```ts
const numbers: number[] = [1, 2, 3, 4, 5];
const evenNumbers: number[] = numbers.filter((num: number) => num % 2 === 0);
console.log(evenNumbers); // [2, 4]
```

### **2.3 reduce()**
Reduces an array to a single value.
```ts
const numbers: number[] = [1, 2, 3, 4];
const sum: number = numbers.reduce((acc: number, num: number) => acc + num, 0);
console.log(sum); // 10
```

### **2.4 forEach()**
Executes a function for each element.
```ts
const numbers: number[] = [1, 2, 3];
numbers.forEach((num: number) => console.log(num));
```

### **2.5 find()**
Finds the first matching element.
```ts
const numbers: number[] = [1, 2, 3, 4];
const firstEven: number | undefined = numbers.find((num: number) => num % 2 === 0);
console.log(firstEven); // 2
```

### **2.6 some()**
Checks if at least one element satisfies a condition.
```ts
const numbers: number[] = [1, 3, 5, 7];
const hasEven: boolean = numbers.some((num: number) => num % 2 === 0);
console.log(hasEven); // false
```

### **2.7 every()**
Checks if all elements satisfy a condition.
```ts
const numbers: number[] = [2, 4, 6];
const allEven: boolean = numbers.every((num: number) => num % 2 === 0);
console.log(allEven); // true
```

### **2.8 sort()**
Sorts an array in place.
```ts
const numbers: number[] = [3, 1, 4, 2];
numbers.sort((a: number, b: number) => a - b);
console.log(numbers); // [1, 2, 3, 4]
```

### **2.9 reverse()**
Reverses an array in place.
```ts
const numbers: number[] = [1, 2, 3, 4];
numbers.reverse();
console.log(numbers); // [4, 3, 2, 1]
```

### **2.10 slice()**
Returns a portion of an array.
```ts
const numbers: number[] = [1, 2, 3, 4, 5];
const sliced: number[] = numbers.slice(1, 4);
console.log(sliced); // [2, 3, 4]
```

### **2.11 splice()**
Modifies an array by adding/removing elements.
```ts
const numbers: number[] = [1, 2, 3, 4];
numbers.splice(1, 2, 99, 100);
console.log(numbers); // [1, 99, 100, 4]
```

### **2.12 join()**
Converts an array into a string.
```ts
const words: string[] = ["Hello", "World"];
console.log(words.join(" ")); // "Hello World"
```

---

## **3. Advanced Topics**

### **3.1 FlatMap()**
Flattens and maps an array.
```ts
const nestedArray: number[][] = [[1, 2], [3, 4]];
const flatMapped: number[] = nestedArray.flatMap(arr => arr);
console.log(flatMapped); // [1, 2, 3, 4]
```

### **3.2 ReduceRight()**
Same as `reduce()` but operates from right to left.
```ts
const numbers: number[] = [1, 2, 3, 4];
const sum: number = numbers.reduceRight((acc: number, num: number) => acc + num, 0);
console.log(sum); // 10
```

### **3.3 Fill()**
Fills an array with a static value.
```ts
const array: number[] = new Array(5).fill(0);
console.log(array); // [0, 0, 0, 0, 0]
```

### **3.4 Includes()**
Checks if an element exists.
```ts
const numbers: number[] = [1, 2, 3, 4];
console.log(numbers.includes(3)); // true
```

---



