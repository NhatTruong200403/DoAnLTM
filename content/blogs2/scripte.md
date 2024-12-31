---
title: "DOM là gì? Các thao tác với DOM trong Javascript"
date: 2023-12-31T12:00:00+07:00
summary: "Tìm hiểu DOM (Document Object Model), cách hoạt động của nó trong JavaScript và các thao tác phổ biến như truy xuất, thay đổi nội dung, thêm hoặc xóa phần tử HTML."
image: /images/script/e.png
---

# DOM là gì? Các thao tác với DOM trong Javascript

## DOM là gì?

**DOM (Document Object Model)** là một giao diện lập trình cho các tài liệu HTML và XML. Nó cung cấp cách để các ngôn ngữ lập trình, như JavaScript, có thể tương tác và thao tác với cấu trúc tài liệu.

### Đặc điểm của DOM:
- Cung cấp cây cấu trúc của tài liệu HTML (DOM Tree).
- Mỗi phần tử HTML, thuộc tính và nội dung trong tài liệu là một nút (Node) trong cây DOM.
- DOM cho phép đọc và thay đổi nội dung, cấu trúc và kiểu của tài liệu.


## Cấu trúc của DOM

DOM tổ chức tài liệu HTML thành một **cây nút (node tree)** gồm:

1. **Document Node**: Đại diện cho toàn bộ tài liệu HTML.
2. **Element Node**: Đại diện cho các thẻ HTML (ví dụ: `<div>`, `<p>`, `<h1>`).
3. **Attribute Node**: Đại diện cho các thuộc tính của thẻ HTML.
4. **Text Node**: Đại diện cho nội dung văn bản bên trong thẻ HTML.

Ví dụ:
```html
<!DOCTYPE html>
<html>
<head>
    <title>DOM Example</title>
</head>
<body>
    <h1>Hello, DOM!</h1>
    <p>This is an example.</p>
</body>
</html>
```
DOM Tree của tài liệu trên:
```
Document
 └── html
     └── head
     |     └── title
     |           └── "DOM Example"
     └── body
           └── h1
           |     └── "Hello, DOM!"
           └── p
                 └── "This is an example."
```

## Các thao tác phổ biến với DOM

### 1. **Truy xuất phần tử**
Sử dụng JavaScript để truy cập các phần tử HTML trong tài liệu DOM.

#### Các phương thức phổ biến:
1. `document.getElementById(id)`: Truy xuất phần tử theo `id`.
   ```javascript
   const element = document.getElementById("myElement");
   console.log(element);
   ```

2. `document.getElementsByClassName(className)`: Truy xuất các phần tử theo tên lớp.
   ```javascript
   const elements = document.getElementsByClassName("myClass");
   console.log(elements);
   ```

3. `document.getElementsByTagName(tagName)`: Truy xuất các phần tử theo tên thẻ.
   ```javascript
   const paragraphs = document.getElementsByTagName("p");
   console.log(paragraphs);
   ```

4. `document.querySelector(selector)`: Truy xuất phần tử đầu tiên phù hợp với bộ chọn CSS.
   ```javascript
   const firstDiv = document.querySelector("div");
   console.log(firstDiv);
   ```

5. `document.querySelectorAll(selector)`: Truy xuất tất cả các phần tử phù hợp với bộ chọn CSS.
   ```javascript
   const allDivs = document.querySelectorAll("div");
   console.log(allDivs);
   ```

### 2. **Thay đổi nội dung và thuộc tính**

#### Thay đổi nội dung văn bản:
Sử dụng thuộc tính `innerHTML` hoặc `textContent`.

```javascript
const heading = document.getElementById("myHeading");
heading.innerHTML = "New Content!";
// Hoặc
heading.textContent = "New Content!";
```

#### Thay đổi thuộc tính:
Sử dụng phương thức `setAttribute` hoặc truy cập trực tiếp.

```javascript
const link = document.querySelector("a");
link.setAttribute("href", "https://example.com");
// Hoặc
link.href = "https://example.com";
```

### 3. **Thêm và xóa phần tử**

#### Thêm phần tử:
Sử dụng `createElement` và `appendChild` hoặc `insertBefore`.

```javascript
const newDiv = document.createElement("div");
newDiv.textContent = "I am a new div!";
document.body.appendChild(newDiv);
```

#### Xóa phần tử:
Sử dụng `removeChild` hoặc `remove`.

```javascript
const unwantedElement = document.getElementById("unwanted");
unwantedElement.remove();
```

### 4. **Thay đổi kiểu dáng (CSS)**

#### Sử dụng thuộc tính `style`:
```javascript
const box = document.getElementById("box");
box.style.backgroundColor = "blue";
box.style.color = "white";
```

#### Thêm hoặc xóa lớp CSS:
```javascript
const button = document.querySelector("button");
button.classList.add("active");
button.classList.remove("inactive");
```

### 5. **Lắng nghe sự kiện (Event)**
Sử dụng `addEventListener` để gắn sự kiện vào phần tử.

```javascript
const button = document.querySelector("button");
button.addEventListener("click", () => {
    alert("Button clicked!");
});
```

## Kết luận
DOM là một công cụ mạnh mẽ giúp JavaScript tương tác với tài liệu HTML. Bằng cách hiểu và sử dụng DOM, bạn có thể xây dựng các trang web tương tác và động một cách dễ dàng.
