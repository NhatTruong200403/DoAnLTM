---
title: "Đối tượng / Object trong Javascript"
date: 2023-12-31T12:00:00+07:00
summary: "Tìm hiểu về đối tượng (Object) trong Javascript, cách tạo và sử dụng các thuộc tính, phương thức, cũng như các thao tác phổ biến với đối tượng."
image: /images/script/f.png
---

# Đối tượng / Object trong Javascript

## **1. Đối tượng trong Javascript là gì?**
Đối tượng (Object) trong Javascript là một kiểu dữ liệu cho phép bạn lưu trữ các cặp "key-value". Mỗi key là một chuỗi hoặc ký hiệu (symbol), và value có thể là bất kỳ kiểu dữ liệu nào, bao gồm cả một đối tượng khác.

### **Ví dụ về đối tượng:**
```javascript
const person = {
  name: "John Doe",
  age: 30,
  isEmployed: true,
  greet: function() {
    console.log("Hello, my name is " + this.name);
  }
};
```

Trong ví dụ trên:
- `name`, `age`, `isEmployed` là **thuộc tính (properties)**.
- `greet` là một **phương thức (method)**.

---

## **2. Cách tạo đối tượng trong Javascript**

### **2.1. Sử dụng cặp dấu ngoặc nhọn {}**
```javascript
const car = {
  brand: "Toyota",
  model: "Corolla",
  year: 2023
};
```

### **2.2. Sử dụng `Object()` constructor**
```javascript
const car = new Object();
car.brand = "Toyota";
car.model = "Corolla";
car.year = 2023;
```

### **2.3. Sử dụng Object.create()**
```javascript
const prototype = {
  greet: function() {
    console.log("Hello!");
  }
};

const newObj = Object.create(prototype);
newObj.name = "John";
```

---

## **3. Truy cập thuộc tính trong đối tượng**
Bạn có thể truy cập thuộc tính bằng cách sử dụng **dấu chấm (dot notation)** hoặc **dấu ngoặc vuông (bracket notation)**.

### **Dấu chấm (dot notation):**
```javascript
console.log(person.name); // "John Doe"
```

### **Dấu ngoặc vuông (bracket notation):**
```javascript
console.log(person["name"]); // "John Doe"
```

---

## **4. Cách thêm, sửa và xóa thuộc tính**

### **4.1. Thêm thuộc tính:**
```javascript
person.gender = "Male";
```

### **4.2. Sửa thuộc tính:**
```javascript
person.age = 35;
```

### **4.3. Xóa thuộc tính:**
```javascript
delete person.isEmployed;
```

---

## **5. Phương thức trong đối tượng**
Phương thức là một hàm được định nghĩa bên trong đối tượng. Chúng ta có thể gọi phương thức bằng cú pháp `objectName.methodName()`.

### **Ví dụ:**
```javascript
const calculator = {
  add: function(a, b) {
    return a + b;
  },
  subtract: function(a, b) {
    return a - b;
  }
};

console.log(calculator.add(5, 3)); // 8
console.log(calculator.subtract(5, 3)); // 2
```

---

## **6. Vòng lặp với đối tượng**

### **6.1. Sử dụng `for...in`:**
```javascript
for (let key in person) {
  console.log(`${key}: ${person[key]}`);
}
```

### **6.2. Sử dụng `Object.keys()`, `Object.values()` và `Object.entries()`:**
- **`Object.keys()`**: Trả về mảng các key.
- **`Object.values()`**: Trả về mảng các giá trị.
- **`Object.entries()`**: Trả về mảng các cặp key-value.

```javascript
console.log(Object.keys(person)); // ["name", "age", "gender"]
console.log(Object.values(person)); // ["John Doe", 35, "Male"]
console.log(Object.entries(person));
// [["name", "John Doe"], ["age", 35], ["gender", "Male"]]
```

---

## **7. Đối tượng lồng nhau**
Đối tượng có thể chứa các đối tượng khác làm thuộc tính.

### **Ví dụ:**
```javascript
const company = {
  name: "TechCorp",
  address: {
    street: "123 Main St",
    city: "New York",
    zipCode: "10001"
  }
};

console.log(company.address.city); // "New York"
```

---

## **8. Một số thao tác nâng cao với đối tượng**

### **8.1. Copy đối tượng:**
Sử dụng `Object.assign()` hoặc spread operator (`...`).
```javascript
const newPerson = Object.assign({}, person);
// Hoặc:
const newPerson2 = { ...person };
```

### **8.2. So sánh đối tượng:**
Đối tượng trong Javascript được so sánh theo tham chiếu, không phải giá trị.
```javascript
const obj1 = { name: "John" };
const obj2 = { name: "John" };
console.log(obj1 === obj2); // false
```

### **8.3. Freeze và Seal đối tượng:**
- **`Object.freeze()`**: Ngăn không cho chỉnh sửa hoặc thêm/xóa thuộc tính.
- **`Object.seal()`**: Ngăn không cho thêm/xóa thuộc tính nhưng cho phép chỉnh sửa giá trị thuộc tính hiện có.
```javascript
Object.freeze(person);
Object.seal(person);
```

---

## **9. Kết luận**
Đối tượng là một phần cốt lõi trong Javascript và rất quan trọng khi xây dựng các ứng dụng phức tạp. Nắm vững cách sử dụng đối tượng, thao tác với thuộc tính, phương thức và các kỹ thuật nâng cao sẽ giúp bạn làm chủ ngôn ngữ này một cách hiệu quả.
