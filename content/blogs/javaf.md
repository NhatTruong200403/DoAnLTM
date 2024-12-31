---
title: "Bảo mật Spring Boot RESTful Service sử dụng Basic Authentication trong Java"
date: 2024-12-30T12:00:00+07:00
summary: Bài viết này sẽ hướng dẫn bạn cách bảo mật một dịch vụ RESTful trong Spring Boot sử dụng Basic Authentication. Chúng ta sẽ cấu hình Spring Security để yêu cầu xác thực khi truy cập vào các endpoint của dịch vụ.
image: /images/java/f.png
---

# Bảo mật Spring Boot RESTful Service sử dụng Basic Authentication trong Java

Khi xây dựng các dịch vụ RESTful với Spring Boot, một yếu tố quan trọng cần lưu ý là bảo mật. Một trong những cách bảo mật đơn giản và phổ biến là sử dụng **Basic Authentication**. Trong bài viết này, chúng ta sẽ tìm hiểu cách cấu hình Basic Authentication cho dịch vụ RESTful trong ứng dụng Spring Boot.

## Basic Authentication là gì?

**Basic Authentication** là một phương thức xác thực trong HTTP, trong đó tên người dùng và mật khẩu được mã hóa theo định dạng Base64 và gửi trong tiêu đề của mỗi yêu cầu HTTP. Dù đơn giản, nhưng Basic Authentication thường được sử dụng trong các ứng dụng không yêu cầu bảo mật quá cao hoặc chỉ dùng trong các môi trường phát triển.

## Các bước thực hiện

### Bước 1: Thêm dependency Spring Security

Để bảo mật ứng dụng của bạn, bạn cần thêm dependency Spring Security vào file `pom.xml` của dự án.

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-security</artifactId>
</dependency>
```
Dependency này sẽ cung cấp các tính năng bảo mật cơ bản cho ứng dụng Spring Boot của bạn, bao gồm Basic Authentication.

### Bước 2: Cấu hình Spring Security
Tạo một lớp cấu hình bảo mật để cấu hình Spring Security và bật tính năng Basic Authentication. Trong lớp cấu hình này, bạn sẽ chỉ định các chi tiết xác thực như người dùng và mật khẩu.

Tạo lớp SecurityConfig.java:

``` java
package com.example.springbootdemo.config;

import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.security.config.annotation.web.builders.HttpSecurity;
import org.springframework.security.config.annotation.web.configuration.EnableWebSecurity;
import org.springframework.security.config.annotation.web.configuration.WebSecurityConfigurerAdapter;
import org.springframework.security.core.userdetails.User;
import org.springframework.security.core.userdetails.UserDetailsService;
import org.springframework.security.core.userdetails.InMemoryUserDetailsManager;
import org.springframework.security.crypto.bcrypt.BCryptPasswordEncoder;
import org.springframework.security.crypto.password.PasswordEncoder;

@Configuration
@EnableWebSecurity
public class SecurityConfig extends WebSecurityConfigurerAdapter {

    @Override
    protected void configure(HttpSecurity http) throws Exception {
        http
            .authorizeRequests()
                .antMatchers("/hello").authenticated()  // Bảo mật endpoint "/hello"
                .anyRequest().permitAll()  // Các endpoint còn lại không yêu cầu xác thực
            .and()
            .httpBasic();  // Kích hoạt Basic Authentication
    }

    @Bean
    @Override
    public UserDetailsService userDetailsService() {
        // Tạo người dùng mặc định với tên người dùng "user" và mật khẩu "password"
        InMemoryUserDetailsManager manager = new InMemoryUserDetailsManager();
        manager.createUser(User.withUsername("user").password(passwordEncoder().encode("password")).roles("USER").build());
        return manager;
    }

    @Bean
    public PasswordEncoder passwordEncoder() {
        return new BCryptPasswordEncoder();  // Mã hóa mật khẩu bằng BCrypt
    }
}
```
Trong lớp cấu hình trên:

- configure(HttpSecurity http) xác định các endpoint nào yêu cầu xác thực. Ví dụ, /hello là endpoint yêu cầu xác thực.
- Phương thức userDetailsService() tạo một người dùng trong bộ nhớ với tên người dùng là user và mật khẩu là password. Mật khẩu được mã hóa sử dụng BCrypt.
- httpBasic() được sử dụng để kích hoạt Basic Authentication.
### Bước 3: Tạo RESTful Service
Bây giờ, chúng ta sẽ tạo một endpoint RESTful để kiểm tra việc xác thực.

Tạo lớp HelloController.java:

```java
package com.example.springbootdemo.controller;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class HelloController {

    @GetMapping("/hello")
    public String sayHello() {
        return "Hello, Spring Boot with Basic Authentication!";
    }
}
```
Lớp HelloController chứa một phương thức sayHello(), trả về một chuỗi khi truy cập vào endpoint /hello.

### Bước 4: Chạy ứng dụng
Bây giờ, bạn có thể chạy ứng dụng Spring Boot của mình. Mở terminal hoặc command prompt và chạy lệnh sau:

```bash
mvn spring-boot:run
```
### Bước 5: Kiểm tra Basic Authentication
Khi ứng dụng đang chạy, mở trình duyệt hoặc công cụ như Postman và truy cập vào endpoint /hello:

```bash
http://localhost:8080/hello
```
Bạn sẽ được yêu cầu nhập tên người dùng và mật khẩu. Nhập user cho tên người dùng và password cho mật khẩu. Nếu bạn nhập chính xác, bạn sẽ nhận được phản hồi:

```csharp
Hello, Spring Boot with Basic Authentication!
```
Nếu bạn không nhập đúng thông tin xác thực, bạn sẽ nhận được thông báo lỗi 401 Unauthorized.

### Kết luận
Chúng ta đã thực hiện một ví dụ cơ bản về cách bảo mật một dịch vụ RESTful trong Spring Boot bằng cách sử dụng Basic Authentication. Đây là một phương thức xác thực đơn giản và dễ triển khai. Tuy nhiên, trong môi trường sản xuất, bạn nên xem xét sử dụng các phương pháp bảo mật mạnh mẽ hơn, chẳng hạn như OAuth2 hoặc JWT.

### Các bước tiếp theo
- Tìm hiểu về OAuth2: Học cách bảo mật ứng dụng sử dụng OAuth2, một phương thức bảo mật mạnh mẽ và phổ biến hơn trong môi trường sản xuất.
- Xác thực với JWT: Tìm hiểu về cách sử dụng JSON Web Tokens (JWT) để bảo mật dịch vụ RESTful trong Spring Boot.
- Spring Security với CORS: Cấu hình Spring Security để hỗ trợ Cross-Origin Resource Sharing (CORS) nếu ứng dụng của bạn phải giao tiếp với các dịch vụ từ các miền khác nhau.

Tài liệu tham khảo
- [Spring Security Documentation](https://docs.spring.io/spring-security/reference/)
- [Spring Boot Documentation](https://docs.spring.io/spring-boot/)