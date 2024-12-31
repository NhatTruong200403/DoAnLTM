---
title: "Cài đặt Spring Boot trong Java và xây dựng dự án cơ bản"
date: 2024-12-30T12:00:00+07:00
summary: Spring Boot là một framework mạnh mẽ giúp phát triển ứng dụng Java nhanh chóng và dễ dàng. Trong bài viết này, chúng ta sẽ tìm hiểu cách cài đặt Spring Boot và tạo một dự án Spring Boot cơ bản, bao gồm việc tạo các API REST đơn giản.
image: /images/java/c.png
---

# Cài đặt Spring Boot trong Java và xây dựng dự án cơ bản

Spring Boot là một phần mở rộng của Spring Framework, giúp việc phát triển các ứng dụng Java trở nên dễ dàng hơn rất nhiều. Với Spring Boot, bạn không cần phải cấu hình các thành phần như servlet container hay các file XML phức tạp. Bài viết này sẽ hướng dẫn bạn cách cài đặt Spring Boot và tạo một dự án Spring Boot cơ bản.

## Các bước cài đặt Spring Boot

### Bước 1: Cài đặt JDK

Để bắt đầu phát triển ứng dụng Spring Boot, bạn cần cài đặt JDK (Java Development Kit) phiên bản 8 trở lên. Bạn có thể tải JDK từ trang chính thức của Oracle hoặc OpenJDK.

- [Tải JDK tại Oracle](https://www.oracle.com/java/technologies/javase-jdk11-downloads.html)
- [Tải OpenJDK](https://adoptopenjdk.net/)

Sau khi cài đặt, bạn có thể kiểm tra phiên bản Java đã cài đặt bằng cách mở terminal hoặc command prompt và chạy lệnh:

```bash
java -version
```
### Bước 2: Cài đặt Maven
Maven là công cụ quản lý dự án và xây dựng phổ biến trong cộng đồng Java. Bạn cần cài đặt Maven để quản lý các thư viện và dependencies cho dự án Spring Boot của bạn.

- [Tải Maven](https://maven.apache.org/download.cgi)
Sau khi cài đặt, kiểm tra Maven bằng lệnh:

```bash
mvn -version
```
### Bước 3: Tạo dự án Spring Boot
Bạn có thể tạo dự án Spring Boot thông qua Spring Initializr, một công cụ trực tuyến giúp tạo dự án Spring Boot nhanh chóng. Truy cập [Spring Initializr](https://start.spring.io/) và thực hiện các bước sau:

1. Chọn Project là Maven hoặc Gradle (Chúng ta sẽ sử dụng Maven trong ví dụ này).
2. Chọn Language là Java.
3. Chọn Spring Boot Version mới nhất.
4. Điền thông tin về Group và Artifact (ví dụ: com.example và springbootdemo).
5. Chọn các dependencies bạn cần, ví dụ như Spring Web, Spring Boot DevTools, Spring Data JPA (nếu cần).
6. Nhấn Generate để tải về file nén chứa dự án Spring Boot.

Giải nén file và mở nó trong IDE yêu thích của bạn (Eclipse, IntelliJ IDEA, VS Code, ...).

### Bước 4: Cấu trúc dự án
Một dự án Spring Boot cơ bản sẽ có cấu trúc thư mục như sau:

```html
springbootdemo/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com/example/springbootdemo/
│   │   │       └── SpringbootdemoApplication.java
│   │   ├── resources/
│   │   │   ├── application.properties
├── pom.xml
```
Trong đó:

- SpringbootdemoApplication.java là lớp khởi động ứng dụng Spring Boot.
- application.properties chứa các cấu hình của ứng dụng.


# Viết mã nguồn cho dự án Spring Boot cơ bản
### Bước 5: Viết lớp khởi động ứng dụng
Mở file SpringbootdemoApplication.java và thêm mã nguồn sau:

```java
package com.example.springbootdemo;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class SpringbootdemoApplication {

    public static void main(String[] args) {
        SpringApplication.run(SpringbootdemoApplication.class, args);
    }
}
```
Lớp SpringbootdemoApplication có chú thích @SpringBootApplication, là một tổ hợp của các chú thích @Configuration, @EnableAutoConfiguration và @ComponentScan. Chú thích này giúp tự động cấu hình và quét các lớp Spring.

### Bước 6: Tạo một REST API đơn giản
Tạo một controller để cung cấp một API REST đơn giản. Tạo một lớp mới có tên HelloController.java trong thư mục com/example/springbootdemo:

```java
package com.example.springbootdemo;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class HelloController {

    @GetMapping("/hello")
    public String sayHello() {
        return "Hello, Spring Boot!";
    }
}
```
Lớp HelloController được chú thích với @RestController, cho phép Spring Boot tự động cung cấp các phương thức này dưới dạng API REST. Phương thức sayHello() sẽ trả về chuỗi "Hello, Spring Boot!" khi người dùng truy cập vào URL /hello.

### Bước 7: Chạy ứng dụng
Mở terminal hoặc command prompt, điều hướng đến thư mục dự án và chạy lệnh sau để xây dựng và chạy ứng dụng:

```bash
mvn spring-boot:run
```
Sau khi ứng dụng khởi động, bạn có thể mở trình duyệt và truy cập vào http://localhost:8080/hello. Bạn sẽ thấy thông báo "Hello, Spring Boot!" trên trình duyệt.

### Kết luận
Chúng ta đã cài đặt thành công Spring Boot và xây dựng một dự án cơ bản với một API REST đơn giản. Spring Boot giúp việc phát triển ứng dụng Java trở nên nhanh chóng và dễ dàng hơn, với các tính năng tự động cấu hình và hỗ trợ mạnh mẽ cho các ứng dụng web. Bạn có thể mở rộng dự án này bằng cách thêm các tính năng như kết nối cơ sở dữ liệu, xác thực người dùng, hoặc triển khai các API phức tạp hơn.