---
title: "Các sự kiện (Event) trong Javascript"
date: 2023-12-31T12:00:00+07:00
summary: "Hiểu rõ về sự kiện trong JavaScript, cách xử lý chúng và các loại sự kiện phổ biến như click, hover, submit. Học cách sử dụng Event Listener để làm cho ứng dụng web trở nên tương tác hơn."
image: /images/script/d.png
---

# Các sự kiện (Event) trong JavaScript

JavaScript cho phép bạn tương tác với người dùng thông qua các **sự kiện** (events). Đây là các hành động hoặc xảy ra khi người dùng tương tác với trình duyệt như nhấp chuột, nhập văn bản, hoặc tải trang.

---

## **1. Sự kiện trong JavaScript là gì?**
Sự kiện là một hành động hoặc một sự kiện xảy ra trong hệ thống. Ví dụ:

- Người dùng nhấn vào một nút.
- Con trỏ di chuyển qua một phần tử.
- Một form được gửi đi.
- Một trang web được tải hoàn toàn.

Các sự kiện là thành phần quan trọng để làm cho trang web trở nên **tương tác**.

---

## **2. Cách xử lý sự kiện trong JavaScript**
Có ba cách chính để xử lý sự kiện trong JavaScript:

### **2.1. Sử dụng thuộc tính HTML**
Bạn có thể thêm sự kiện trực tiếp vào HTML bằng cách sử dụng các thuộc tính sự kiện như `onclick`, `onmouseover`,...

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <title>Sự kiện trong HTML</title>
</head>
<body>
  <button onclick="alert('Bạn đã nhấn nút!')">Nhấn tôi</button>
</body>
</html>
```

### **2.2. Gắn sự kiện trực tiếp vào JavaScript**
Sử dụng cú pháp gắn sự kiện trực tiếp thông qua JavaScript:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <title>Thêm sự kiện bằng JS</title>
</head>
<body>
  <button id="myButton">Nhấn tôi</button>

  <script>
    const button = document.getElementById('myButton');
    button.onclick = function() {
      alert('Bạn đã nhấn nút!');
    };
  </script>
</body>
</html>
```

### **2.3. Sử dụng phương thức `addEventListener`**
Đây là cách linh hoạt và hiện đại nhất để xử lý sự kiện.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <title>addEventListener Example</title>
</head>
<body>
  <button id="myButton">Nhấn tôi</button>

  <script>
    const button = document.getElementById('myButton');
    button.addEventListener('click', function() {
      alert('Bạn đã nhấn nút!');
    });
  </script>
</body>
</html>
```

---

## **3. Các loại sự kiện phổ biến trong JavaScript**

### **3.1. Sự kiện chuột (Mouse Events)**
- `click`: Xảy ra khi nhấp vào phần tử.
- `dblclick`: Xảy ra khi nhấp đúp.
- `mousedown`: Khi nút chuột được nhấn xuống.
- `mouseup`: Khi nhả nút chuột.
- `mousemove`: Khi di chuyển chuột qua phần tử.
- `mouseover`: Khi con trỏ chuột đi vào phần tử.

Ví dụ:
```html
<div id="box" style="width:100px; height:100px; background-color:lightblue;"></div>
<script>
  const box = document.getElementById('box');
  box.addEventListener('mouseover', function() {
    box.style.backgroundColor = 'yellow';
  });
  box.addEventListener('mouseout', function() {
    box.style.backgroundColor = 'lightblue';
  });
</script>
```

### **3.2. Sự kiện bàn phím (Keyboard Events)**
- `keydown`: Khi nhấn phím xuống.
- `keyup`: Khi nhả phím.
- `keypress`: Khi nhấn và giữ phím (không được khuyến nghị vì đã lỗi thời).

Ví dụ:
```html
<input type="text" id="inputField" placeholder="Nhập văn bản">
<script>
  const input = document.getElementById('inputField');
  input.addEventListener('keydown', function(event) {
    console.log(`Phím bạn nhấn: ${event.key}`);
  });
</script>
```

### **3.3. Sự kiện Form (Form Events)**
- `submit`: Khi gửi form.
- `change`: Khi giá trị của phần tử thay đổi.
- `focus`: Khi phần tử được chọn.
- `blur`: Khi phần tử mất tiêu điểm.

Ví dụ:
```html
<form id="myForm">
  <input type="text" placeholder="Tên của bạn">
  <button type="submit">Gửi</button>
</form>
<script>
  const form = document.getElementById('myForm');
  form.addEventListener('submit', function(event) {
    event.preventDefault(); // Ngăn chặn gửi form mặc định
    alert('Form đã được gửi!');
  });
</script>
```

### **3.4. Sự kiện cửa sổ (Window Events)**
- `load`: Khi trang hoặc tài nguyên được tải.
- `resize`: Khi kích thước cửa sổ thay đổi.
- `scroll`: Khi trang được cuộn.
- `unload`: Khi rời khỏi trang (không khuyến nghị).

Ví dụ:
```html
<script>
  window.addEventListener('resize', function() {
    console.log(`Kích thước cửa sổ: ${window.innerWidth}x${window.innerHeight}`);
  });
</script>
```

---

## **4. Sử dụng sự kiện tùy chỉnh (Custom Events)**
JavaScript cũng cho phép bạn tạo và kích hoạt sự kiện tùy chỉnh.

### **Tạo sự kiện tùy chỉnh**
```javascript
const customEvent = new Event('myCustomEvent');
const element = document.getElementById('myElement');

// Lắng nghe sự kiện
element.addEventListener('myCustomEvent', function() {
  alert('Sự kiện tùy chỉnh đã được kích hoạt!');
});

// Kích hoạt sự kiện
element.dispatchEvent(customEvent);
```

---

## **5. Kết luận**

Sự kiện trong JavaScript giúp bạn xây dựng các trang web tương tác, cải thiện trải nghiệm người dùng. Hiểu và sử dụng đúng cách xử lý sự kiện sẽ giúp bạn làm chủ việc phát triển web một cách chuyên nghiệp.