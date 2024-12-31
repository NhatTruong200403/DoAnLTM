---
title: "Giới thiệu về Spring Boot Actuator trong ứng dụng Spring Boot"
date: 2024-12-30T12:00:00+07:00
summary: Spring Boot Actuator cung cấp các tính năng giám sát và quản lý cho các ứng dụng Spring Boot, giúp dễ dàng theo dõi và quản lý trạng thái của ứng dụng trong môi trường sản xuất. Bài viết này giới thiệu về các tính năng chính của Spring Boot Actuator và cách sử dụng chúng.
image: /images/java/e.png
---

# Giới thiệu về Spring Boot Actuator trong ứng dụng Spring Boot

Spring Boot Actuator là một phần mở rộng của Spring Boot, cung cấp một loạt các tính năng giúp giám sát và quản lý ứng dụng trong môi trường sản xuất. Nó giúp bạn theo dõi các thông số quan trọng của ứng dụng, như hiệu suất, sức khỏe, các thông tin cấu hình, và các thông số hệ thống khác mà không cần phải cài đặt thêm phần mềm giám sát phức tạp.

Spring Boot Actuator cung cấp nhiều điểm cuối RESTful (endpoints) mà bạn có thể truy cập để thu thập các thông tin về ứng dụng của mình.

## Các tính năng chính của Spring Boot Actuator

### 1. **Health Check**

Một trong những tính năng quan trọng của Spring Boot Actuator là cung cấp endpoint `/actuator/health`. Endpoint này giúp kiểm tra tình trạng của ứng dụng (health status). Bạn có thể xác định trạng thái sức khỏe của ứng dụng, bao gồm các thành phần như cơ sở dữ liệu, hệ thống file, và các tài nguyên phụ thuộc khác.

**Cấu hình trong `application.properties`:**
```properties
management.endpoint.health.show-details=always
```
Truy cập endpoint health:

```bash
http://localhost:8080/actuator/health

```
Endpoint này sẽ trả về các thông tin chi tiết về trạng thái của ứng dụng.

### 2. Metrics
Spring Boot Actuator cung cấp thông tin về các chỉ số (metrics) của ứng dụng, như số lượng yêu cầu HTTP, thời gian phản hồi, lượng bộ nhớ sử dụng, và các số liệu khác liên quan đến hiệu suất. Các chỉ số này có thể giúp bạn theo dõi hiệu suất và điều chỉnh ứng dụng của mình.

Truy cập endpoint metrics:

```bash
http://localhost:8080/actuator/metrics
```
Endpoint này sẽ trả về các chỉ số khác nhau như jvm.memory.used, http.server.requests, v.v.

### 3. Environment
Spring Boot Actuator cũng cung cấp một endpoint /actuator/env để truy xuất các thông tin cấu hình môi trường của ứng dụng, bao gồm các thuộc tính trong file application.properties hoặc application.yml.

Truy cập endpoint environment:

```bash
http://localhost:8080/actuator/env
```
Endpoint này giúp bạn kiểm tra các cấu hình của ứng dụng và các thuộc tính môi trường.

### 4. Application Info
Thông qua Spring Boot Actuator, bạn có thể lấy các thông tin về ứng dụng của mình như tên ứng dụng, phiên bản, và các thông tin tùy chỉnh khác được định nghĩa trong file cấu hình.

Truy cập endpoint info:

```bash
http://localhost:8080/actuator/info
```
Endpoint này sẽ trả về thông tin về ứng dụng của bạn.

### 5. Audit Events
Spring Boot Actuator cung cấp một endpoint /actuator/auditevents để ghi lại các sự kiện kiểm tra (audit events) trong ứng dụng. Điều này rất hữu ích để theo dõi các hành động quan trọng hoặc sự thay đổi trong hệ thống.

Truy cập endpoint audit events:

```bash
http://localhost:8080/actuator/auditevents
```
### 6. Loggers
Bạn có thể sử dụng Spring Boot Actuator để thay đổi cấu hình logger của ứng dụng thông qua endpoint /actuator/loggers. Điều này cho phép bạn theo dõi mức độ log của các lớp cụ thể và thay đổi chúng ngay lập tức.

Truy cập endpoint loggers:

```bash
http://localhost:8080/actuator/loggers
```
Cài đặt Spring Boot Actuator
Để sử dụng Spring Boot Actuator trong ứng dụng của bạn, bạn cần thêm dependency vào file pom.xml của dự án:

Cấu hình trong pom.xml:

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-actuator</artifactId>
</dependency>
```
Sau khi thêm dependency này vào, Spring Boot Actuator sẽ tự động kích hoạt các tính năng giám sát và quản lý cho ứng dụng của bạn.

Bảo mật và Cấu hình các Endpoint
Mặc dù Spring Boot Actuator rất hữu ích trong việc giám sát ứng dụng, nhưng các endpoint này cần được bảo vệ trong môi trường sản xuất để tránh việc lộ thông tin nhạy cảm. Bạn có thể cấu hình bảo mật cho các endpoint này bằng cách sử dụng Spring Security.

Cấu hình bảo mật trong application.properties:

```properties
management.endpoints.web.exposure.include=health,info
management.endpoint.health.show-details=never
```
Cấu hình trên chỉ cho phép truy cập các endpoint health và info, đồng thời ẩn các thông tin chi tiết về sức khỏe của ứng dụng.

### Kết luận
Spring Boot Actuator cung cấp một bộ công cụ mạnh mẽ để giám sát và quản lý các ứng dụng Spring Boot trong môi trường sản xuất. Các tính năng như kiểm tra sức khỏe, chỉ số hiệu suất, cấu hình môi trường, và ghi lại các sự kiện kiểm tra giúp bạn dễ dàng theo dõi trạng thái của ứng dụng và cải thiện hiệu suất, bảo mật. Tuy nhiên, cần lưu ý bảo vệ các endpoint để tránh rủi ro bảo mật trong quá trình triển khai ứng dụng.

### Các bước tiếp theo
1. Tìm hiểu thêm về bảo mật Spring Boot Actuator: Học cách bảo vệ các endpoint của Actuator bằng cách cấu hình Spring Security.
1. Giám sát với các công cụ ngoài Spring Boot Actuator: Tìm hiểu cách tích hợp Spring Boot Actuator với các công cụ giám sát như Prometheus hoặc Grafana.
3. Tùy chỉnh các endpoint: Học cách tùy chỉnh các endpoint của Actuator để đáp ứng nhu cầu giám sát đặc thù của ứng dụng.
Tài liệu tham khảo
- [Spring Boot Actuator Documentation](https://docs.spring.io/spring-boot/index.html)
- [Spring Boot Actuator Endpoints](https://docs.spring.io/spring-boot/index.html)

Chúc bạn thành công trong việc sử dụng Spring Boot Actuator để giám sát và quản lý ứng dụng của mình!