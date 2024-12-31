---
title: "Function trong Javascript - Cách tạo hàm và gọi hàm trong JS"
date: 2023-12-31T12:00:00+07:00
summary: "Tìm hiểu chi tiết về function trong JavaScript: cách tạo hàm, gọi hàm, và các kiểu hàm khác nhau như hàm thông thường, hàm ẩn danh, hàm mũi tên. Học cách sử dụng các tham số, đối số và các từ khóa đặc biệt như return."
image: /images/script/c.png
---

# Function trong Javascript - Cách tạo hàm và gọi hàm trong JS

## 1. **Khái niệm Function trong JavaScript**
Hàm (function) trong JavaScript là một khối mã thực thi các tác vụ cụ thể hoặc trả về giá trị. Hàm giúp tái sử dụng mã, tổ chức code rõ ràng hơn, và giảm thiểu lỗi.

### **Cú pháp cơ bản của hàm trong JavaScript:**
```javascript
function functionName(parameters) {
    // code to be executed
}
```

### **Ví dụ:**
```javascript
function sayHello() {
    console.log("Hello, World!");
}
```

---

## 2. **Cách gọi hàm (Function Call)**
Sau khi định nghĩa hàm, bạn cần gọi nó để thực thi.

### **Ví dụ:**
```javascript
sayHello(); // Output: Hello, World!
```

Bạn có thể gọi hàm nhiều lần:
```javascript
sayHello(); // Output: Hello, World!
sayHello(); // Output: Hello, World!
```

---

## 3. **Hàm với tham số (Parameters) và đối số (Arguments)**

### **Tham số:**
Là các biến được định nghĩa trong dấu ngoặc tròn khi khai báo hàm.

### **Đối số:**
Là giá trị được truyền vào khi gọi hàm.

### **Ví dụ:**
```javascript
function greet(name) {
    console.log("Hello, " + name);
}

greet("Alice"); // Output: Hello, Alice
greet("Bob");   // Output: Hello, Bob
```

Hàm có thể có nhiều tham số:
```javascript
function add(a, b) {
    return a + b;
}

console.log(add(5, 3)); // Output: 8
```

---

## 4. **Từ khóa `return` trong hàm**
Từ khóa `return` trả về giá trị từ hàm. Khi gặp `return`, việc thực thi hàm dừng lại.

### **Ví dụ:**
```javascript
function multiply(a, b) {
    return a * b;
}

let result = multiply(4, 5);
console.log(result); // Output: 20
```

Hàm không có `return` sẽ trả về `undefined`:
```javascript
function noReturn() {
    console.log("No return here");
}

console.log(noReturn()); // Output: No return here \n undefined
```

---

## 5. **Hàm ẩn danh (Anonymous Function)**
Hàm không có tên, thường được sử dụng khi cần một hàm tạm thời.

### **Ví dụ:**
```javascript
let greet = function(name) {
    return "Hello, " + name;
};

console.log(greet("Charlie")); // Output: Hello, Charlie
```

---

## 6. **Hàm mũi tên (Arrow Function)**
Cú pháp ngắn gọn hơn cho khai báo hàm, giới thiệu từ ES6.

### **Cú pháp:**
```javascript
const functionName = (parameters) => {
    // code to be executed
};
```

### **Ví dụ:**
```javascript
const add = (a, b) => a + b;
console.log(add(10, 20)); // Output: 30
```

Hàm mũi tên với một tham số và một biểu thức:
```javascript
const square = x => x * x;
console.log(square(5)); // Output: 25
```

---

## 7. **Default Parameters (Tham số mặc định)**
Bạn có thể đặt giá trị mặc định cho tham số trong hàm.

### **Ví dụ:**
```javascript
function greet(name = "Guest") {
    console.log("Hello, " + name);
}

greet();          // Output: Hello, Guest
greet("Alice");  // Output: Hello, Alice
```

---

## 8. **Hàm lồng nhau (Nested Functions)**
Một hàm có thể chứa hàm khác bên trong.

### **Ví dụ:**
```javascript
function outerFunction(outerVariable) {
    function innerFunction(innerVariable) {
        console.log(`Outer: ${outerVariable}, Inner: ${innerVariable}`);
    }
    innerFunction("Inner Value");
}

outerFunction("Outer Value"); // Output: Outer: Outer Value, Inner: Inner Value
```

---

## 9. **IIFE (Immediately Invoked Function Expression)**
Hàm tự động thực thi ngay sau khi được định nghĩa.

### **Ví dụ:**
```javascript
(function() {
    console.log("IIFE executed");
})();

// Output: IIFE executed
```

IIFE thường dùng để tạo scope cục bộ.

---

## 10. **Hàm là đối tượng bậc nhất (First-Class Object)**
Trong JavaScript, hàm được coi là đối tượng bậc nhất, có thể:
- Gán cho biến
- Truyền làm đối số
- Trả về từ hàm khác

### **Ví dụ:**
Gán hàm cho biến:
```javascript
const sayHi = function() {
    console.log("Hi!");
};

sayHi(); // Output: Hi!
```

Truyền hàm làm đối số:
```javascript
function executeFunction(fn) {
    fn();
}

executeFunction(() => console.log("Function executed"));
// Output: Function executed
```

---

## 11. **Kết luận**
Hàm trong JavaScript là một công cụ mạnh mẽ giúp tổ chức và tái sử dụng mã. Hiểu rõ cách tạo và gọi hàm sẽ giúp bạn viết code hiệu quả hơn và dễ bảo trì.
