---
title: "Các thuộc tính của Spring Boot trong Java"
date: 2024-12-30T12:00:00+07:00
summary: Spring Boot cung cấp rất nhiều thuộc tính cấu hình để tùy chỉnh và tối ưu hóa ứng dụng. Trong bài viết này, chúng ta sẽ khám phá các thuộc tính quan trọng của Spring Boot và cách sử dụng chúng.
image: /images/java/d.png
---

# Các thuộc tính của Spring Boot trong Java

Spring Boot là một framework mạnh mẽ được xây dựng để giúp lập trình viên nhanh chóng tạo ra các ứng dụng Java có thể triển khai. Một trong những điểm mạnh của Spring Boot chính là khả năng cấu hình tự động, giúp giảm bớt khối lượng công việc cần làm trong việc cấu hình ứng dụng. Tuy nhiên, đôi khi bạn cần điều chỉnh các thuộc tính cấu hình để tùy chỉnh và tối ưu hóa ứng dụng của mình.

Trong bài viết này, chúng ta sẽ tìm hiểu một số thuộc tính quan trọng của Spring Boot và cách sử dụng chúng.

## Các thuộc tính cấu hình trong Spring Boot

### 1. `server.port`

Thuộc tính này được sử dụng để cấu hình cổng mà ứng dụng Spring Boot sẽ chạy trên đó. Mặc định, Spring Boot sẽ sử dụng cổng `8080`. Tuy nhiên, bạn có thể thay đổi nó trong file `application.properties` hoặc `application.yml`.

**Cấu hình trong `application.properties`:**
```properties
server.port=8081
```
Cấu hình trong application.yml:

```yaml
server:
  port: 8081
```
### 2. `spring.datasource.url`
Thuộc tính này được sử dụng để cấu hình kết nối đến cơ sở dữ liệu trong Spring Boot. Bạn có thể chỉ định URL của cơ sở dữ liệu mà ứng dụng sẽ kết nối.

Cấu hình trong application.properties:

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/mydb
spring.datasource.username=root
spring.datasource.password=root
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
```

### 3. `spring.datasource.driver-class-name`
Thuộc tính này xác định tên lớp driver của cơ sở dữ liệu mà bạn sử dụng. Ví dụ, nếu bạn sử dụng MySQL, bạn sẽ cần cấu hình com.mysql.cj.jdbc.Driver.

Cấu hình trong application.properties:

```properties
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
```
### 4. `spring.jpa.hibernate.ddl-auto`
Thuộc tính này được sử dụng để tự động tạo bảng trong cơ sở dữ liệu hoặc thay đổi cấu trúc cơ sở dữ liệu khi ứng dụng khởi động. Các giá trị phổ biến của thuộc tính này bao gồm:

- none: Không tự động thay đổi cấu trúc cơ sở dữ liệu.
- update: Tự động cập nhật cơ sở dữ liệu.
- create: Tạo lại cơ sở dữ liệu mỗi khi ứng dụng khởi động lại.
- create-drop: Tạo lại cơ sở dữ liệu và xóa khi ứng dụng dừng.
- Cấu hình trong application.properties:

```properties
spring.jpa.hibernate.ddl-auto=update
```
### 5. `spring.application.name`
Thuộc tính này được sử dụng để đặt tên cho ứng dụng. Nó rất hữu ích trong môi trường microservices để xác định ứng dụng khi triển khai và giám sát.

Cấu hình trong application.properties:

```properties
spring.application.name=MySpringBootApp
```
### 6. `logging.level`
Thuộc tính này cho phép bạn cấu hình mức độ log cho ứng dụng. Bạn có thể thiết lập mức độ log cho từng package hoặc lớp cụ thể như DEBUG, INFO, WARN, hoặc ERROR.

Cấu hình trong application.properties:

```properties
logging.level.org.springframework=INFO
logging.level.com.example.springbootdemo=DEBUG
```
### 7. `server.servlet.context-path`
Thuộc tính này giúp bạn cấu hình đường dẫn gốc (context path) cho ứng dụng. Mặc định, ứng dụng Spring Boot chạy ở root (/), nhưng nếu bạn muốn thay đổi nó, có thể sử dụng thuộc tính này.

Cấu hình trong application.properties:

```properties
server.servlet.context-path=/myapp
```   
### 8. `spring.profiles.active`
Thuộc tính này cho phép bạn kích hoạt một profile cấu hình cụ thể trong môi trường Spring Boot. Ví dụ, bạn có thể tạo các file cấu hình cho môi trường dev, test, và prod.

Cấu hình trong application.properties:

```properties
spring.profiles.active=dev
```
Với cấu hình trên, Spring Boot sẽ tự động tải file application-dev.properties nếu bạn tạo file này trong dự án của mình.

### Kết luận
Spring Boot cung cấp rất nhiều thuộc tính cấu hình để giúp lập trình viên tối ưu hóa ứng dụng và đáp ứng các yêu cầu môi trường khác nhau. Việc hiểu rõ các thuộc tính này và cách sử dụng chúng là rất quan trọng trong quá trình phát triển ứng dụng.

Chúng ta đã khám phá một số thuộc tính quan trọng như cấu hình cổng, kết nối cơ sở dữ liệu, mức độ log, và các profile cấu hình. Bạn có thể áp dụng chúng vào dự án của mình để cải thiện hiệu suất và khả năng mở rộng của ứng dụng Spring Boot.

### Các bước tiếp theo
1. Tìm hiểu thêm về Spring Boot Profiles: Các profile cấu hình giúp ứng dụng hoạt động linh hoạt trong các môi trường khác nhau (ví dụ: phát triển, thử nghiệm, và sản xuất).
2. Tối ưu hóa cấu hình Spring Boot: Học cách tối ưu hóa các thuộc tính cấu hình cho hiệu suất và bảo mật tốt hơn.
3. Tích hợp Spring Boot với các công cụ giám sát: Tìm hiểu cách tích hợp Spring Boot với các công cụ như Prometheus hoặc ELK stack để theo dõi và phân tích ứng dụng.
Tài liệu tham khảo
- [Spring Boot Documentation](https://docs.spring.io/spring-boot/)
- [Spring Boot Properties Reference](https://docs.spring.io/spring-boot/index.html)

Chúc bạn thành công trong việc tìm hiểu và áp dụng các thuộc tính của Spring Boot vào ứng dụng của mình!





