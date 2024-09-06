---
authors: ["Trần Trung Nguyên"]
title: Lập trình với Go: Thư viện `io`
date: 2024-09-06
description: Hướng dẫn sử dụng thư viện 'io' trong lập trình Go
categories:
  - Lập trình với Go
tags:
  - Go
  - Lập trình
---
# Giới thiệu về package `io`

Thư viện `io` trong Go cung cấp các giao diện *(interface)* và hàm liên quan đến việc đọc, ghi dữ liệu, cùng các thao tác nhập xuất cơ bản. Nó là một phần quan trọng trong việc làm việc với luồng dữ liệu, cho phép lập trình viên xử lý các tác vụ như đọc từ file, ghi ra mạng, hoặc thao tác với buffer mà không cần quan tâm đến chi tiết cài đặt.
# `io.Reader`

`io.Reader` là một trong những interface cơ bản và phổ biến nhất trong Go. Interface này định nghĩa một phương thức duy nhất là `Read`, cho phép đọc dữ liệu từ một nguồn vào một slice byte `[]byte`. Mọi thứ từ đọc file, đọc từ mạng, hay bất kỳ nguồn dữ liệu nào đều có thể được thực hiện qua `io.Reader`.

```go
type Reader interface {
	Read(p []byte) (n int, err error)
}
```
Phương thức `Read` sẽ đọc dữ liệu vào slice `p`, trả về số byte đã đọc và lỗi nếu có. Các thành phần phổ biến như `os.File`, `bytes.Buffer`, hay `net.Conn` đều thực hiện interface `io.Reader`.


# `io.Writer`

Tương tự, `io.Writer` định nghĩa hành vi của các đối tượng có thể ghi dữ liệu ra một luồng nào đó, ví dụ như ghi vào file, buffer, hoặc gửi dữ liệu qua mạng. `io.Writer` cũng chỉ có một phương thức duy nhất là `Write`.

```go
type Writer interface {
    Write(p []byte) (n int, err error)
}
```

Phương thức `Write` ghi dữ liệu từ slice `p` ra nguồn đích và trả về số byte đã ghi cùng lỗi nếu có. Tương tự như `io.Reader`, các thành phần như `os.File`, `bytes.Buffer`, và `net.Conn` đều thực hiện interface `io.Writer`.

*Còn tiếp*