---
title: "Các toán tử trong JavaScript"
date: 2023-12-31T12:00:00+07:00
summary: JavaScript cung cấp nhiều loại toán tử giúp thao tác với dữ liệu. Bài viết này sẽ tổng hợp các loại toán tử và cung cấp ví dụ minh họ.
image: /images/script/b.png
---

# Các toán tử trong JavaScript

## Giới thiệu
JavaScript cung cấp một bộ các toán tử phong phú giúp thực hiện các tác vụ trên dữ liệu như tính toán, so sánh, logic, và gán giá trị. Hiểu rõ các loại toán tử là bước quan trọng trong việc lập trình với JavaScript.


## **1. Toán tử số học (Arithmetic Operators)**
Toán tử số học được sử dụng để thực hiện các phép tính toán cơ bản.

| Toán tử | Ký hiệu | Ví dụ           | Kết quả |
|------------|---------|----------------|----------|
| Cộng      | `+`     | `5 + 3`        | `8`      |
| Trừ        | `-`     | `10 - 7`       | `3`      |
| Nhân       | `*`     | `4 * 2`        | `8`      |
| Chia       | `/`     | `20 / 5`       | `4`      |
| Chia dư    | `%`     | `10 % 3`       | `1`      |
| Lũy thừa  | `**`    | `2 ** 3`       | `8`      |


## **2. Toán tử gán (Assignment Operators)**
Toán tử gán được sử dụng để gán giá trị cho biến.

| Toán tử | Ký hiệu | Ví dụ           | Kết quả |
|------------|---------|----------------|----------|
| Gán        | `=`     | `x = 10`       | `x = 10` |
| Cộng bổ sung | `+=`    | `x += 5`       | `x = x + 5` |
| Trừ bổ sung  | `-=`    | `x -= 2`       | `x = x - 2` |
| Nhân bổ sung | `*=`    | `x *= 3`       | `x = x * 3` |
| Chia bổ sung  | `/=`    | `x /= 2`       | `x = x / 2` |
| Chia dư bổ sung | `%=`    | `x %= 4`       | `x = x % 4` |


## **3. Toán tử so sánh (Comparison Operators)**
Toán tử so sánh được sử dụng để so sánh hai giá trị.

| Toán tử          | Ký hiệu | Ví dụ        | Kết quả |
|--------------------|---------|---------------|----------|
| Bằng             | `==`    | `5 == 5`      | `true`   |
| Khác             | `!=`    | `5 != 4`      | `true`   |
| Lớn hơn         | `>`     | `6 > 3`       | `true`   |
| Nhỏ hơn         | `<`     | `3 < 4`       | `true`   |
| Lớn hơn hoặc bằng | `>=`    | `5 >= 5`      | `true`   |
| Nhỏ hơn hoặc bằng | `<=`    | `3 <= 4`      | `true`   |

 **Lưu ý**: Toán tử `===` và `!==` so sánh cả kiểu dữ liệu.


## **4. Toán tử logic (Logical Operators)**
Toán tử logic được sử dụng để kết hợp các biểu thức logic.

| Toán tử    | Ký hiệu | Ví dụ               | Kết quả |
|------------|---------|--------------------|----------|
| Và         | `&&`    | `true && false`   | `false`  |
| Hoặc      | `||`    | `true || false`   | `true`   |
| Phủ định  | `!`     | `!true`           | `false`  |


## **5. Toán tử tăng, giảm (Increment and Decrement)**
Toán tử tăng giảm được dùng để tăng hoặc giảm giá trị của biến.

| Toán tử     | Ký hiệu | Ví dụ     | Kết quả |
|-------------|---------|----------|----------|
| Tăng trước  | `++x`    | `let x = 5; ++x` | `x = 6`  |
| Tăng sau    | `x++`    | `let x = 5; x++` | `x = 6`  |
| Giảm trước  | `--x`    | `let x = 5; --x` | `x = 4`  |
| Giảm sau    | `x--`    | `let x = 5; x--` | `x = 4`  |


## **6. Toán tử bit (Bitwise Operators)**
Toán tử bit hoạt động trên các bit nhị trong số nguyên.

| Toán tử | Ký hiệu | Ví dụ          | Kết quả |
|----------|---------|---------------|----------|
| AND      | `&`     | `5 & 1`       | `1`      |
| OR       | `|`     | `5 | 1`       | `5`      |
| XOR      | `^`     | `5 ^ 1`       | `4`      |
| NOT      | `~`     | `~5`          | `-6`     |
| Shift L  | `<<`    | `5 << 1`      | `10`     |
| Shift R  | `>>`    | `5 >> 1`      | `2`      |


## **7. Toán tử khác**

- **Toán tử 3 ngôi (Ternary Operator):**

  - Cú pháp: `condition ? value1 : value2`
  - Ví dụ:

    ```javascript
    let result = (5 > 3) ? 'Greater' : 'Smaller';
    console.log(result); // Output: Greater
    ```

- **Toán tử typeof:**

  - Xác định kiểu dữ liệu.
  - Ví dụ:

    ```javascript
    console.log(typeof 42); // Output: number
    ```


## Kết luận
Nắm vững các toán tử trong JavaScript là yếu tố quan trọng để xây dựng các chương trình hiệu quả và dễ dàng bảo trì. Hy vọng bài viết này giúp bạn đọi mới kiến thức về các toán tử và áp dụng trong thực tế.
