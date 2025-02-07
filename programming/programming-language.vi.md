Tổng hợp nhanh về các ngôn ngữ lập trình phổ biến gồm: Java, JavaScript, C#, Python, Go, và PHP.

---
## Bảng nội dung

<!-- TOC -->
* [0. Tổng quan](#0-tổng-quan)
* [1. Quy tắc viết](#1-quy-tắc-viết)
* [2. Cú pháp cơ bản](#2-cú-pháp-cơ-bản)
* [3. Kiểu dữ liệu & Toán tử](#3-kiểu-dữ-liệu--toán-tử)
* [4. Cấu trúc điều kiện & vòng lặp](#4-cấu-trúc-điều-kiện--vòng-lặp)
* [5. Hàm & Đệ quy](#5-hàm--đệ-quy)
* [6. Lập trình hướng đối tượng (OOP)](#6-lập-trình-hướng-đối-tượng-oop)
* [7. Lập trình hàm (Functional Programming)](#7-lập-trình-hàm-functional-programming)
* [8. Xử lý ngoại lệ (Exception Handling)](#8-xử-lý-ngoại-lệ-exception-handling)
* [9. Xử lý chuỗi (String Handling)](#9-xử-lý-chuỗi-string-handling)
* [10. Xử lý mảng (Array Handling)](#10-xử-lý-mảng-array-handling)
* [11. Xử lý danh sách (List Handling)](#11-xử-lý-danh-sách-list-handling)
* [12. Xử lý tập hợp (Set Handling)](#12-xử-lý-tập-hợp-set-handling)
* [13. Xử lý ánh xạ (Dictionary/Map Handling)](#13-xử-lý-ánh-xạ-dictionarymap-handling)
* [14. Xử lý JSON (JSON Handling)](#14-xử-lý-json-json-handling)
* [15. Xử lý tệp (File Handling)](#15-xử-lý-tệp-file-handling)
* [16. Xử lý đồng thời (Concurrency Handling)](#16-xử-lý-đồng-thời-concurrency-handling)
<!-- TOC -->

---

# 0. Tổng quan

| **Hạng mục**                     | **Java**                                       | **JavaScript**                                                | **C#**                               | **Python**                                     | **Go**                                              | **PHP**                            |
|----------------------------------|------------------------------------------------|---------------------------------------------------------------|--------------------------------------|------------------------------------------------|-----------------------------------------------------|------------------------------------|
| **Loại ngôn ngữ**                | Hướng đối tượng, biên dịch nhưng chạy trên JVM | Hướng sự kiện, thông dịch, chạy trên trình duyệt hoặc Node.js | Hướng đối tượng, biên dịch trên .NET | Hướng đối tượng, thông dịch, chạy trên CPython | Ngôn ngữ hệ thống, biên dịch trực tiếp thành mã máy | Hướng đối tượng, thông dịch        |
| **Paradigm (Mô hình lập trình)** | OOP, Functional, Concurrent                    | OOP, Functional, Prototype-based                              | OOP, Functional, Concurrent          | OOP, Functional, Procedural                    | Procedural, Concurrent                              | OOP, Functional, Procedural        |
| **Cách biên dịch/chạy**          | Dịch sang bytecode chạy trên JVM               | Thông dịch trực tiếp hoặc biên dịch với WebAssembly           | Biên dịch thành mã máy trên nền .NET | Thông dịch từng dòng hoặc biên dịch với PyPy   | Biên dịch trực tiếp thành mã máy                    | Thông dịch trực tiếp trên máy chủ  |
| **Hệ sinh thái chính**           | Spring, Hibernate, Jakarta EE                  | Node.js, React, Angular                                       | .NET, ASP.NET, Blazor                | Django, Flask, PyTorch, Pandas                 | Standard Library, gRPC, Fiber                       | Laravel, Symfony, CodeIgniter      |
| **Ứng dụng chính**               | Backend, Android, Enterprise                   | Web Frontend, Backend (Node.js)                               | Enterprise, Game, Web                | AI, Data Science, Web, Scripting               | Hệ thống, Cloud, Backend hiệu suất cao              | Web backend, CMS                   |
| **Cộng đồng & Phát triển**       | Rộng lớn, hỗ trợ mạnh mẽ                       | Phổ biến trên web, hỗ trợ mạnh mẽ                             | Chủ yếu trong doanh nghiệp & game    | Rất phổ biến trong AI & Data                   | Được Google hỗ trợ mạnh mẽ                          | Rất phổ biến trong web development |
| **Hệ điều hành hỗ trợ**          | Windows, macOS, Linux                          | Mọi nền tảng có trình duyệt hoặc Node.js                      | Windows, macOS, Linux                | Windows, macOS, Linux                          | Windows, macOS, Linux                               | Windows, macOS, Linux              |

**Chú thích:**

- OOP (Object-Oriented Programming - Lập trình hướng đối tượng): Mô hình lập trình dựa trên các đối tượng (objects), trong đó dữ liệu và hành vi được đóng gói bên trong các lớp (classes). Các nguyên tắc chính của OOP gồm: Kế thừa (Inheritance), Đa hình (Polymorphism), Đóng gói (Encapsulation), và Trừu tượng hóa (Abstraction).
- Functional Programming (Lập trình hàm): Phong cách lập trình coi các hàm là đối tượng bậc nhất, có thể truyền vào các hàm khác hoặc trả về một hàm khác. Các ngôn ngữ như JavaScript, Python hỗ trợ lập trình hàm với các khái niệm như map(), reduce(), lambda function.
- Prototype-based Programming (Lập trình dựa trên nguyên mẫu): Một mô hình trong JavaScript, trong đó các đối tượng kế thừa từ một nguyên mẫu (prototype) thay vì từ một lớp cố định như trong OOP.
- Concurrent Programming (Lập trình đồng thời): Cho phép nhiều đoạn mã chạy song song (concurrency). Các ngôn ngữ như Java, C#, Go có cơ chế hỗ trợ đa luồng (threads), Goroutines (Go), hay async/await (JavaScript, Python).
- JVM (Java Virtual Machine): Một máy ảo cho phép chương trình Java chạy trên nhiều nền tảng mà không cần biên dịch lại. JVM chuyển đổi bytecode thành mã máy thực thi.
- CLR (.NET Common Language Runtime): Máy ảo của .NET, tương tự JVM nhưng dành riêng cho C# và các ngôn ngữ .NET.
- CPython: Trình thông dịch Python tiêu chuẩn, dịch từng dòng mã thành bytecode và thực thi.
- WebAssembly (WASM): Một định dạng bytecode hiệu suất cao giúp JavaScript chạy nhanh hơn trong trình duyệt bằng cách biên dịch trước.
- Spring, Hibernate, Jakarta EE: Các framework phổ biến của Java để phát triển ứng dụng web và quản lý cơ sở dữ liệu.
- Node.js: Môi trường chạy JavaScript ngoài trình duyệt, giúp xây dựng backend nhanh chóng với kiến trúc non-blocking.
- ASP.NET, Blazor: Các framework phát triển web của Microsoft dành cho C#.
- Django, Flask, PyTorch: Các thư viện mạnh mẽ trong Python, hỗ trợ phát triển web và AI.
- Go Standard Library: Thư viện tiêu chuẩn của Go, cung cấp các công cụ mạnh mẽ để phát triển hệ thống và backend.

[Lên đầu](#bảng-nội-dung)

---

# 1. Quy tắc viết

| **Quy tắc**           | **Java**   | **JavaScript** | **C#**     | **Python**      | **Go**     | **PHP**        |
|-----------------------|------------|----------------|------------|-----------------|------------|----------------|
| **Đặt tên biến**      | camelCase  | camelCase      | camelCase  | snake_case      | camelCase  | snake_case     |
| **Đặt tên hàm**       | camelCase  | camelCase      | PascalCase | snake_case      | camelCase  | snake_case     |
| **Đặt tên lớp**       | PascalCase | PascalCase     | PascalCase | PascalCase      | PascalCase | PascalCase     |
| **Khoảng trắng**      | 4 spaces   | 2 spaces       | 4 spaces   | 4 spaces        | Tabs       | 4 spaces       |
| **Dấu chấm phẩy (;)** | Bắt buộc   | Không bắt buộc | Bắt buộc   | Không dùng      | Không dùng | Không bắt buộc |
| **Khối lệnh**         | `{}`       | `{}`           | `{}`       | Indentation     | `{}`       | `{}`           |


[Lên đầu](#bảng-nội-dung)

---

# 2. Cú pháp cơ bản

| **Hạng mục**                 | **Java**                                      | **JavaScript**                                                     | **C#**                                                          | **Python**                                  | **Go**                                        | **PHP**                                       |
|------------------------------|-----------------------------------------------|--------------------------------------------------------------------|-----------------------------------------------------------------|---------------------------------------------|-----------------------------------------------|-----------------------------------------------|
| **Khai báo biến**            | `int x = 10;`                                 | `let x = 10;` / `const x = 10;`                                    | `int x = 10;`                                                   | `x = 10`                                    | `var x int = 10`                              | `$x = 10;`                                    |
| **Khai báo hằng số**         | `final int X = 100;`                          | `const X = 100;`                                                   | `const int X = 100;`                                            | `X = 100` (không thể thay đổi nếu viết hoa) | `const X = 100`                               | `define("X", 100);`                           |
| **Kiểu dữ liệu cơ bản**      | `int, double, char, boolean, String`          | `Number, String, Boolean, Object, Undefined, Null, Symbol, BigInt` | `int, double, char, bool, string`                               | `int, float, str, bool`                     | `int, float64, string, bool`                  | `int, float, string, bool, array`             |
| **Khai báo mảng**            | `int[] arr = {1, 2, 3};`                      | `let arr = [1, 2, 3];`                                             | `int[] arr = {1, 2, 3};`                                        | `arr = [1, 2, 3]`                           | `arr := []int{1, 2, 3}`                       | `$arr = array(1, 2, 3);`                      |
| **Danh sách (List)**         | `List<Integer> list = new ArrayList<>();`     | `let list = [1, 2, 3];`                                            | `List<int> list = new List<int>() {1, 2, 3};`                   | `list = [1, 2, 3]`                          | `var list = []int{1, 2, 3}`                   | `$list = [1, 2, 3];`                          |
| **Từ điển (Dictionary/Map)** | `Map<String, Integer> map = new HashMap<>();` | `let obj = {"a": 1, "b": 2};`                                      | `Dictionary<string, int> dict = new Dictionary<string, int>();` | `dict = {"a": 1, "b": 2}`                   | `map := map[string]int{"a": 1, "b": 2}`       | `$dict = ["a" => 1, "b" => 2];`               |
| **Tuple**                    | Không hỗ trợ                                  | Không hỗ trợ                                                       | `(int, string) tuple = (1, "hello");`                           | `t = (1, "hello")`                          | Không hỗ trợ                                  | Không hỗ trợ                                  |
| **Set (Tập hợp)**            | `Set<Integer> set = new HashSet<>();`         | Không có                                                           | `HashSet<int> set = new HashSet<int>();`                        | `s = {1, 2, 3}`                             | Không hỗ trợ                                  | Không hỗ trợ                                  |
| **Khai báo hàm**             | `int sum(int a, int b) { return a + b; }`     | `function sum(a, b) { return a + b; }`                             | `int Sum(int a, int b) => a + b;`                               | `def sum(a, b): return a + b`               | `func sum(a int, b int) int { return a + b }` | `function sum($a, $b) { return $a + $b; }`    |
| **Hàm ẩn danh (Lambda)**     | `x -> x * x`                                  | `(x) => x * x`                                                     | `x => x * x`                                                    | `lambda x: x * x`                           | `func(x int) int { return x * x }`            | `$square = function($x) { return $x * $x; };` |

**Chú thích:**
- **Biến (Variable)**: Đại diện cho một giá trị có thể thay đổi trong chương trình.
- **Hằng số (Constant)**: Giá trị không thể thay đổi sau khi được gán.
- **Kiểu dữ liệu (Data Types)**: Xác định loại giá trị mà một biến có thể chứa. Ví dụ, `int` cho số nguyên, `string` cho chuỗi.
- **Mảng (Array)**: Cấu trúc dữ liệu chứa danh sách các phần tử có cùng kiểu.
- **Danh sách (List)**: Tương tự mảng nhưng có thể thay đổi kích thước linh hoạt.
- **Từ điển (Dictionary/Map)**: Cấu trúc dữ liệu lưu trữ các cặp key-value.
- **Tuple**: Một tập hợp không thay đổi, có thể chứa nhiều kiểu dữ liệu khác nhau.
- **Set (Tập hợp)**: Một tập hợp các giá trị duy nhất, không có phần tử trùng lặp.
- **Hàm (Function)**: Một khối mã thực hiện một công việc cụ thể và có thể trả về giá trị.
- **Hàm ẩn danh (Lambda)**: Một hàm không có tên, thường dùng trong lập trình hàm.

[Lên đầu](#bảng-nội-dung)

---

# 3. Kiểu dữ liệu & Toán tử

| **Hạng mục**                 | **Java**                      | **JavaScript**      | **C#**                | **Python**                    | **Go**                     | **PHP**                       |
|------------------------------|-------------------------------|---------------------|-----------------------|-------------------------------|----------------------------|-------------------------------|
| **Số nguyên (Integer)**      | `int x = 10;`                 | `let x = 10;`       | `int x = 10;`         | `x = 10`                      | `var x int = 10`           | `$x = 10;`                    |
| **Số thực (Floating-point)** | `double x = 10.5;`            | `let x = 10.5;`     | `double x = 10.5;`    | `x = 10.5`                    | `var x float64 = 10.5`     | `$x = 10.5;`                  |
| **Chuỗi (String)**           | `String s = "Hello";`         | `let s = "Hello";`  | `string s = "Hello";` | `s = "Hello"`                 | `var s string = "Hello"`   | `$s = "Hello";`               |
| **Boolean**                  | `boolean flag = true;`        | `let flag = true;`  | `bool flag = true;`   | `flag = True`                 | `var flag bool = true`     | `$flag = true;`               |
| **Null / Undefined**         | `null`                        | `null / undefined`  | `null`                | `None`                        | `nil`                      | `null`                        |
| **Ép kiểu tường minh**       | `(double) x`                  | `Number(x)`         | `(double)x`           | `float(x)`                    | `float64(x)`               | `(float) $x;`                 |
| **Ép kiểu ngầm định**        | Tự động nếu không mất dữ liệu | Chuỗi + Số = Chuỗi  | Tự động nếu an toàn   | Tự động nếu không mất dữ liệu | Không hỗ trợ, phải ép kiểu | Tự động nếu không mất dữ liệu |
| **Toán tử số học**           | `+ - * / % ++ --`             | `+ - * / % ++ --`   | `+ - * / % ++ --`     | `+ - * / %`                   | `+ - * / %`                | `+ - * / % ++ --`             |
| **Toán tử logic**            | `&&                           |                     | !`                    | `&&                           |                            | !`                            | `&& || !` | `and, or, not` | `&& || !` | `&& || !` |
| **Toán tử so sánh**          | `== != > < >= <=`             | `== != > < >= <=`   | `== != > < >= <=`     | `== != > < >= <=`             | `== != > < >= <=`          | `== != > < >= <=`             |
| **Toán tử gán**              | `= += -= *= /= %=`            | `= += -= *= /= %=`  | `= += -= *= /= %=`    | `= += -= *= /= %=`            | `= += -= *= /= %=`         | `= += -= *= /= %=`            |
| **Toán tử bitwise**          | `&                            | ^ ~ << >>`          | `&                    | ^ ~ << >>`                    | `&                         | ^ ~ << >>`                    | `& | ^ ~ << >>` | `& | ^ &^ << >>` | `& | ^ ~ << >>` |
| **Toán tử 3 ngôi**           | `condition ? a : b`           | `condition ? a : b` | `condition ? a : b`   | `a if condition else b`       | Không hỗ trợ               | `condition ? a : b;`          |

**Chú thích**
- **Số nguyên (Integer)**: Đại diện cho các số nguyên, không có phần thập phân.
- **Số thực (Floating-point)**: Đại diện cho các số có phần thập phân, thường dùng kiểu `double` hoặc `float`.
- **Chuỗi (String)**: Một dãy ký tự, thường được đặt trong dấu nháy đôi `"..."` hoặc nháy đơn `'...'`.
- **Boolean**: Giá trị đúng hoặc sai (`true / false`).
- **Null / Undefined**: Đại diện cho giá trị không xác định hoặc không tồn tại.
- **Ép kiểu tường minh (Explicit Casting)**: Chuyển đổi kiểu dữ liệu theo cách thủ công, ví dụ từ số nguyên sang số thực.
- **Ép kiểu ngầm định (Implicit Casting)**: Hệ thống tự động chuyển đổi kiểu dữ liệu khi không có mất mát thông tin.
- **Toán tử số học (Arithmetic Operators)**: Thực hiện các phép toán cơ bản như cộng, trừ, nhân, chia, chia lấy dư.
- **Toán tử logic (Logical Operators)**: Dùng để kết hợp các điều kiện logic (`AND`, `OR`, `NOT`).
- **Toán tử so sánh (Comparison Operators)**: Dùng để so sánh hai giá trị (`==`, `!=`, `>`, `<`, `>=`, `<=`).
- **Toán tử gán (Assignment Operators)**: Dùng để gán giá trị cho biến (`=`, `+=`, `-=`, `*=`, `/=`, `%=`).
- **Toán tử bitwise (Bitwise Operators)**: Thao tác trực tiếp trên các bit nhị phân của số (`&`, `|`, `^`, `~`, `<<`, `>>`).
- **Toán tử 3 ngôi (Ternary Operator)**: Một cách rút gọn để viết câu lệnh `if-else`.

[Lên đầu](#bảng-nội-dung)

---

# 4. Cấu trúc điều kiện & vòng lặp

| **Hạng mục**            | **Java**                                         | **JavaScript**                                   | **C#**                                           | **Python**                      | **Go**                                   | **PHP**                                           |
|-------------------------|--------------------------------------------------|--------------------------------------------------|--------------------------------------------------|---------------------------------|------------------------------------------|---------------------------------------------------|
| **Câu lệnh if**         | `if (x > 0) { ... }`                             | `if (x > 0) { ... }`                             | `if (x > 0) { ... }`                             | `if x > 0:`                     | `if x > 0 { ... }`                       | `if ($x > 0) { ... }`                             |
| **Câu lệnh if-else**    | `if (x > 0) { ... } else { ... }`                | `if (x > 0) { ... } else { ... }`                | `if (x > 0) { ... } else { ... }`                | `if x > 0: ... else: ...`       | `if x > 0 { ... } else { ... }`          | `if ($x > 0) { ... } else { ... }`                |
| **Câu lệnh if-else if** | `if (x > 0) { ... } else if (x < 0) { ... }`     | `if (x > 0) { ... } else if (x < 0) { ... }`     | `if (x > 0) { ... } else if (x < 0) { ... }`     | `if x > 0: ... elif x < 0: ...` | `if x > 0 { ... } else if x < 0 { ... }` | `if ($x > 0) { ... } elseif ($x < 0) { ... }`     |
| **Câu lệnh switch**     | `switch (x) { case 1: ... break; default: ... }` | `switch (x) { case 1: ... break; default: ... }` | `switch (x) { case 1: ... break; default: ... }` | Không có, dùng `if-elif-else`   | `switch x { case 1: ... default: ... }`  | `switch ($x) { case 1: ... break; default: ... }` |
| **Vòng lặp for**        | `for (int i = 0; i < 10; i++) { ... }`           | `for (let i = 0; i < 10; i++) { ... }`           | `for (int i = 0; i < 10; i++) { ... }`           | `for i in range(10): ...`       | `for i := 0; i < 10; i++ { ... }`        | `for ($i = 0; $i < 10; $i++) { ... }`             |
| **Vòng lặp foreach**    | `for (int num : array) { ... }`                  | `for (let num of array) { ... }`                 | `foreach (int num in array) { ... }`             | `for num in array: ...`         | `for _, num := range array { ... }`      | `foreach ($array as $num) { ... }`                |
| **Vòng lặp while**      | `while (x > 0) { ... }`                          | `while (x > 0) { ... }`                          | `while (x > 0) { ... }`                          | `while x > 0: ...`              | `for x > 0 { ... }`                      | `while ($x > 0) { ... }`                          |
| **Vòng lặp do-while**   | `do { ... } while (x > 0);`                      | Không có                                         | `do { ... } while (x > 0);`                      | Không có                        | Không có                                 | `do { ... } while ($x > 0);`                      |
| **Break**               | `break;`                                         | `break;`                                         | `break;`                                         | `break`                         | `break`                                  | `break;`                                          |
| **Continue**            | `continue;`                                      | `continue;`                                      | `continue;`                                      | `continue`                      | `continue`                               | `continue;`                                       |

**Chú thích**
- **Câu lệnh if**: Dùng để kiểm tra một điều kiện và thực thi một đoạn mã nếu điều kiện đúng.
- **Câu lệnh if-else**: Thực thi đoạn mã khác khi điều kiện trong `if` không thỏa mãn.
- **Câu lệnh if-else if**: Kiểm tra nhiều điều kiện liên tiếp, khi một điều kiện đúng thì khối mã tương ứng sẽ được thực thi.
- **Câu lệnh switch**: Một cách thay thế cho nhiều `if-else if`, giúp kiểm tra giá trị của biến và thực thi khối mã tương ứng với từng trường hợp (`case`).
- **Vòng lặp for**: Lặp với số lần xác định, thường dùng biến đếm (`i`).
- **Vòng lặp foreach**: Lặp qua từng phần tử trong danh sách, thường dùng với mảng hoặc danh sách.
- **Vòng lặp while**: Lặp khi một điều kiện còn đúng.
- **Vòng lặp do-while**: Giống `while`, nhưng luôn thực thi ít nhất một lần trước khi kiểm tra điều kiện.
- **Break**: Thoát khỏi vòng lặp hoặc `switch`.
- **Continue**: Bỏ qua phần còn lại của vòng lặp hiện tại và tiếp tục vòng lặp kế tiếp.

[Lên đầu](#bảng-nội-dung)

---

# 5. Hàm & Đệ quy

| **Hạng mục**                              | **Java**                                                     | **JavaScript**                                                | **C#**                                                       | **Python**                                             | **Go**                                                                 | **PHP**                                                         |
|-------------------------------------------|--------------------------------------------------------------|---------------------------------------------------------------|--------------------------------------------------------------|--------------------------------------------------------|------------------------------------------------------------------------|-----------------------------------------------------------------|
| **Khai báo hàm**                          | `int sum(int a, int b) { return a + b; }`                    | `function sum(a, b) { return a + b; }`                        | `int Sum(int a, int b) { return a + b; }`                    | `def sum(a, b): return a + b`                          | `func sum(a int, b int) int { return a + b }`                          | `function sum($a, $b) { return $a + $b; }`                      |
| **Hàm void (không trả về)**               | `void printHello() { System.out.println("Hello"); }`         | `function printHello() { console.log("Hello"); }`             | `void PrintHello() { Console.WriteLine("Hello"); }`          | `def print_hello(): print("Hello")`                    | `func printHello() { fmt.Println("Hello") }`                           | `function printHello() { echo "Hello"; }`                       |
| **Hàm với giá trị mặc định**              | `int add(int a, int b = 5) { return a + b; }` (Java 8+)      | `function add(a, b = 5) { return a + b; }`                    | `int Add(int a, int b = 5) { return a + b; }`                | `def add(a, b=5): return a + b`                        | Không hỗ trợ (dùng `varargs`)                                          | `function add($a, $b = 5) { return $a + $b; }`                  |
| **Hàm có số lượng tham số không cố định** | `int sum(int... numbers) { ... }`                            | `function sum(...numbers) { ... }`                            | `int Sum(params int[] numbers) { ... }`                      | `def sum(*numbers): ...`                               | `func sum(numbers ...int) { ... }`                                     | `function sum(...$numbers) { ... }`                             |
| **Hàm ẩn danh (Lambda)**                  | `(x) -> x * x`                                               | `(x) => x * x`                                                | `(x) => x * x`                                               | `lambda x: x * x`                                      | `func(x int) int { return x * x }`                                     | `fn($x) => $x * $x;`                                            |
| **Đệ quy**                                | `int fact(int n) { return (n == 0) ? 1 : n * fact(n - 1); }` | `function fact(n) { return (n == 0) ? 1 : n * fact(n - 1); }` | `int Fact(int n) { return (n == 0) ? 1 : n * Fact(n - 1); }` | `def fact(n): return 1 if n == 0 else n * fact(n - 1)` | `func fact(n int) int { if n == 0 { return 1 } return n * fact(n-1) }` | `function fact($n) { return $n == 0 ? 1 : $n * fact($n - 1); }` |

**Chú thích**
- **Hàm (Function)**: Một khối mã có thể được gọi nhiều lần, có thể nhận tham số và trả về giá trị.
- **Hàm void (Không trả về)**: Hàm không có giá trị trả về, chỉ thực hiện tác vụ nào đó.
- **Giá trị mặc định (Default Parameter Value)**: Nếu một tham số không được truyền vào, nó sẽ có giá trị mặc định.
- **Tham số không cố định (Variadic Function)**: Hàm có thể nhận số lượng tham số thay đổi.
- **Hàm ẩn danh (Lambda Function)**: Hàm không có tên, thường được sử dụng ngắn gọn.
- **Đệ quy (Recursion)**: Hàm gọi lại chính nó để giải quyết bài toán lặp.

[Lên đầu](#bảng-nội-dung)

---

# 6. Lập trình hướng đối tượng (OOP)

| **Hạng mục**                               | **Java**                           | **JavaScript**                            | **C#**                       | **Python**                                   | **Go**                              | **PHP**                                                   |
|--------------------------------------------|------------------------------------|-------------------------------------------|------------------------------|----------------------------------------------|-------------------------------------|-----------------------------------------------------------|
| **Khai báo lớp (Class)**                   | `class Person {}`                  | `class Person {}`                         | `class Person {}`            | `class Person:`                              | `type Person struct {}`             | `class Person {}`                                         |
| **Thuộc tính (Properties)**                | `String name;`                     | `constructor(name) { this.name = name; }` | `public string Name;`        | `def __init__(self, name): self.name = name` | `Name string`                       | `public $name;`                                           |
| **Phương thức (Methods)**                  | `void sayHello() {}`               | `sayHello() {}`                           | `void SayHello() {}`         | `def say_hello(self):`                       | `func (p Person) SayHello() {}`     | `function sayHello() {}`                                  |
| **Tạo đối tượng (Object)**                 | `Person p = new Person();`         | `let p = new Person();`                   | `Person p = new Person();`   | `p = Person()`                               | `p := Person{}`                     | `$p = new Person();`                                      |
| **Từ khóa `this`**                         | `this.name`                        | `this.name`                               | `this.Name`                  | `self.name`                                  | `p.Name`                            | `$this->name`                                             |
| **Tính kế thừa (Inheritance)**             | `class Employee extends Person {}` | `class Employee extends Person {}`        | `class Employee : Person {}` | `class Employee(Person):`                    | `type Employee struct { Person }`   | `class Employee extends Person {}`                        |
| **Ghi đè phương thức (Method Overriding)** | `@Override`                        | `methodName() {}` (ghi đè tự động)        | `override`                   | `def method_name(self):` (ghi đè tự động)    | `func (e Employee) MethodName() {}` | `function methodName() {}` (dùng `parent::methodName();`) |
| **Đa hình (Polymorphism)**                 | Hỗ trợ                             | Hỗ trợ                                    | Hỗ trợ                       | Hỗ trợ                                       | Hỗ trợ (dựa trên interface)         | Hỗ trợ                                                    |
| **Lớp trừu tượng (Abstract Class)**        | `abstract class Animal {}`         | Không có (dùng interface)                 | `abstract class Animal {}`   | `from abc import ABC`                        | Không có (dùng interface)           | `abstract class Animal {}`                                |
| **Giao diện (Interface)**                  | `interface Animal {}`              | Không có (dùng class)                     | `interface IAnimal {}`       | Không có (dùng abstract class)               | `type Animal interface {}`          | `interface Animal {}`                                     |
| **Đóng gói (Encapsulation)**               | `private String name;`             | Không có (quy ước `_name`)                | `private string name;`       | `self._name`                                 | `private name string`               | `private $name;`                                          |

**Chú thích**
- **Lớp (Class)**: Khuôn mẫu để tạo ra các đối tượng, chứa thuộc tính và phương thức.
- **Thuộc tính (Properties)**: Biến bên trong lớp, lưu trữ dữ liệu của đối tượng.
- **Phương thức (Methods)**: Hàm bên trong lớp, thực hiện hành động của đối tượng.
- **Tạo đối tượng (Object Creation)**: Cách khởi tạo một thể hiện của lớp.
- **Từ khóa `this`**: Dùng để tham chiếu đến chính đối tượng hiện tại.
- **Kế thừa (Inheritance)**: Lớp con kế thừa thuộc tính và phương thức từ lớp cha.
- **Ghi đè phương thức (Method Overriding)**: Lớp con cung cấp cách triển khai khác cho phương thức của lớp cha.
- **Đa hình (Polymorphism)**: Một phương thức có thể hoạt động khác nhau tùy theo lớp con triển khai nó.
- **Lớp trừu tượng (Abstract Class)**: Lớp không thể khởi tạo, chỉ có thể được kế thừa.
- **Giao diện (Interface)**: Một hợp đồng quy định các phương thức mà một lớp phải triển khai.
- **Đóng gói (Encapsulation)**: Giới hạn quyền truy cập vào các thành phần của lớp để bảo vệ dữ liệu.

[Lên đầu](#bảng-nội-dung)

---

# 7. Lập trình hàm (Functional Programming)

| **Hạng mục**                            | **Java**                                                               | **JavaScript**                    | **C#**                                             | **Python**                                                      | **Go**                                                  | **PHP**                                         |
|-----------------------------------------|------------------------------------------------------------------------|-----------------------------------|----------------------------------------------------|-----------------------------------------------------------------|---------------------------------------------------------|-------------------------------------------------|
| **Hàm bậc cao (Higher-order function)** | `Function<Integer, Integer> square = x -> x * x;`                      | `const square = x => x * x;`      | `Func<int, int> square = x => x * x;`              | `square = lambda x: x * x`                                      | `func square(x int) int { return x * x }`               | `function square($x) { return $x * $x; }`       |
| **Hàm ẩn danh (Lambda Function)**       | `(x) -> x * x`                                                         | `(x) => x * x`                    | `(x) => x * x`                                     | `lambda x: x * x`                                               | `func(x int) int { return x * x }`                      | `fn($x) => $x * $x;`                            |
| **Map (ánh xạ)**                        | `list.stream().map(x -> x * 2).collect(Collectors.toList())`           | `arr.map(x => x * 2);`            | `arr.Select(x => x * 2).ToList();`                 | `list(map(lambda x: x * 2, arr))`                               | `slices.Map(arr, func(x int) int { return x * 2 })`     | `array_map(fn($x) => $x * 2, $arr);`            |
| **Filter (lọc)**                        | `list.stream().filter(x -> x > 5).collect(Collectors.toList())`        | `arr.filter(x => x > 5);`         | `arr.Where(x => x > 5).ToList();`                  | `list(filter(lambda x: x > 5, arr))`                            | `slices.Filter(arr, func(x int) bool { return x > 5 })` | `array_filter($arr, fn($x) => $x > 5);`         |
| **Reduce (tích lũy)**                   | `list.stream().reduce(0, (a, b) -> a + b);`                            | `arr.reduce((a, b) => a + b, 0);` | `arr.Aggregate(0, (a, b) => a + b);`               | `from functools import reduce; reduce(lambda a, b: a + b, arr)` | Không hỗ trợ trực tiếp                                  | `array_reduce($arr, fn($a, $b) => $a + $b, 0);` |
| **Currying**                            | `Function<Integer, Function<Integer, Integer>> add = a -> b -> a + b;` | `const add = a => b => a + b;`    | `Func<int, Func<int, int>> add = a => b => a + b;` | `def add(a): return lambda b: a + b`                            | Không hỗ trợ trực tiếp                                  | Không hỗ trợ trực tiếp                          |
| **Lazy Evaluation**                     | `Stream<Integer> s = Stream.of(1, 2, 3).map(x -> x * x);`              | `const s = arr.map(x => x * x);`  | `arr.Select(x => x * x);`                          | `map(lambda x: x * x, arr)`                                     | Không hỗ trợ trực tiếp                                  | Không hỗ trợ trực tiếp                          |

**Chú thích**
- **Hàm bậc cao (Higher-order function)**: Hàm nhận một hàm khác làm tham số hoặc trả về một hàm khác.
- **Hàm ẩn danh (Lambda Function)**: Hàm không có tên, thường được dùng trong lập trình hàm.
- **Map (ánh xạ)**: Dùng để biến đổi từng phần tử của danh sách.
- **Filter (lọc)**: Chọn lọc các phần tử thỏa mãn điều kiện.
- **Reduce (tích lũy)**: Gộp các phần tử thành một giá trị duy nhất.
- **Currying**: Biến một hàm nhận nhiều tham số thành một chuỗi hàm nhận từng tham số một.
- **Lazy Evaluation**: Trì hoãn việc thực thi cho đến khi giá trị thực sự cần thiết.

[Lên đầu](#bảng-nội-dung)

---

# 8. Xử lý ngoại lệ (Exception Handling)

| **Hạng mục**           | **Java**                                                  | **JavaScript**                                  | **C#**                                                          | **Python**                                                                 | **Go**                                                   | **PHP**                                                    |
|------------------------|-----------------------------------------------------------|-------------------------------------------------|-----------------------------------------------------------------|----------------------------------------------------------------------------|----------------------------------------------------------|------------------------------------------------------------|
| **Try-Catch**          | `try { ... } catch (Exception e) { ... }`                 | `try { ... } catch (e) { ... }`                 | `try { ... } catch (Exception e) { ... }`                       | `try: ... except Exception as e:`                                          | `defer func() { if r := recover(); r != nil { ... } }()` | `try { ... } catch (Exception $e) { ... }`                 |
| **Finally**            | `try { ... } catch (Exception e) { ... } finally { ... }` | `try { ... } catch (e) { ... } finally { ... }` | `try { ... } catch (Exception e) { ... } finally { ... }`       | `try: ... finally: ...`                                                    | Không có `finally`, dùng `defer`                         | `try { ... } catch (Exception $e) { ... } finally { ... }` |
| **Throw Exception**    | `throw new Exception("Error");`                           | `throw new Error("Error");`                     | `throw new Exception("Error");`                                 | `raise Exception("Error")`                                                 | `panic("Error")`                                         | `throw new Exception("Error");`                            |
| **Tạo ngoại lệ riêng** | `class MyException extends Exception {}`                  | `class MyException extends Error {}`            | `class MyException : Exception {}`                              | `class MyException(Exception):`                                            | Không có, dùng `error` interface                         | `class MyException extends Exception {}`                   |
| **Bắt nhiều ngoại lệ** | `try { ... } catch (IOException                           | SQLException e) { ... }`                        | `try { ... } catch (e) { if (e instanceof TypeError) { ... } }` | `try { ... } catch (IOException e) { ... } catch (SQLException e) { ... }` | `try: ... except (IOError, ValueError) as e:`            | Không hỗ trợ trực tiếp, dùng `recover()`                   | `try { ... } catch (TypeError | ValueError $e) { ... }` |

**Chú thích**
- **Try-Catch**: Dùng để xử lý lỗi có thể xảy ra mà không làm dừng chương trình.
- **Finally**: Luôn được thực thi, dù có xảy ra ngoại lệ hay không.
- **Throw Exception**: Dùng để tạo ra một ngoại lệ và kết thúc chương trình hoặc nhảy vào `catch`.
- **Tạo ngoại lệ riêng**: Tạo lớp ngoại lệ tùy chỉnh kế thừa từ lớp ngoại lệ có sẵn.
- **Bắt nhiều ngoại lệ**: Xử lý nhiều loại ngoại lệ khác nhau bằng nhiều `catch`.

[Lên đầu](#bảng-nội-dung)

---

# 9. Xử lý chuỗi (String Handling)

| **Hạng mục**                | **Java**              | **JavaScript**         | **C#**                | **Python**            | **Go**                            | **PHP**                      |
|-----------------------------|-----------------------|------------------------|-----------------------|-----------------------|-----------------------------------|------------------------------|
| **Khai báo chuỗi**          | `String s = "Hello";` | `let s = "Hello";`     | `string s = "Hello";` | `s = "Hello"`         | `s := "Hello"`                    | `$s = "Hello";`              |
| **Nối chuỗi**               | `"Hello " + "World"`  | `"Hello " + "World"`   | `"Hello " + "World"`  | `"Hello " + "World"`  | `"Hello " + "World"`              | `"Hello " . "World"`         |
| **Độ dài chuỗi**            | `s.length()`          | `s.length`             | `s.Length`            | `len(s)`              | `len(s)`                          | `strlen($s)`                 |
| **Truy cập ký tự**          | `s.charAt(0)`         | `s[0]`                 | `s[0]`                | `s[0]`                | `s[0]`                            | `$s[0]`                      |
| **Cắt chuỗi (Substring)**   | `s.substring(1, 4)`   | `s.slice(1, 4)`        | `s.Substring(1, 3)`   | `s[1:4]`              | `s[1:4]`                          | `substr($s, 1, 3)`           |
| **Tách chuỗi (Split)**      | `s.split(" ")`        | `s.split(" ")`         | `s.Split(' ')`        | `s.split(" ")`        | `strings.Split(s, " ")`           | `explode(" ", $s)`           |
| **Chuyển thành chữ hoa**    | `s.toUpperCase()`     | `s.toUpperCase()`      | `s.ToUpper()`         | `s.upper()`           | `strings.ToUpper(s)`              | `strtoupper($s)`             |
| **Chuyển thành chữ thường** | `s.toLowerCase()`     | `s.toLowerCase()`      | `s.ToLower()`         | `s.lower()`           | `strings.ToLower(s)`              | `strtolower($s)`             |
| **Loại bỏ khoảng trắng**    | `s.trim()`            | `s.trim()`             | `s.Trim()`            | `s.strip()`           | `strings.TrimSpace(s)`            | `trim($s)`                   |
| **Thay thế chuỗi**          | `s.replace("l", "x")` | `s.replace(/l/g, "x")` | `s.Replace("l", "x")` | `s.replace("l", "x")` | `strings.ReplaceAll(s, "l", "x")` | `str_replace("l", "x", $s)`  |
| **Kiểm tra chuỗi con**      | `s.contains("He")`    | `s.includes("He")`     | `s.Contains("He")`    | `"He" in s`           | `strings.Contains(s, "He")`       | `strpos($s, "He") !== false` |

**Chú thích**
- **Khai báo chuỗi**: Cách tạo một chuỗi trong từng ngôn ngữ.
- **Nối chuỗi**: Kết hợp hai hoặc nhiều chuỗi thành một chuỗi duy nhất.
- **Độ dài chuỗi**: Lấy số ký tự trong chuỗi.
- **Truy cập ký tự**: Lấy ký tự tại một vị trí cụ thể trong chuỗi.
- **Cắt chuỗi (Substring)**: Trích xuất một phần của chuỗi.
- **Tách chuỗi (Split)**: Chia chuỗi thành danh sách dựa trên ký tự phân tách.
- **Chuyển thành chữ hoa/chữ thường**: Biến đổi chữ cái trong chuỗi thành chữ hoa hoặc chữ thường.
- **Loại bỏ khoảng trắng**: Xóa khoảng trắng ở đầu và cuối chuỗi.
- **Thay thế chuỗi**: Thay thế một phần của chuỗi bằng nội dung khác.
- **Kiểm tra chuỗi con**: Kiểm tra xem chuỗi có chứa một chuỗi khác hay không.

[Lên đầu](#bảng-nội-dung)

---

# 10. Xử lý mảng (Array Handling)

| **Hạng mục**         | **Java**                                                  | **JavaScript**                      | **C#**                                    | **Python**                           | **Go**                                                  | **PHP**                                         |
|----------------------|-----------------------------------------------------------|-------------------------------------|-------------------------------------------|--------------------------------------|---------------------------------------------------------|-------------------------------------------------|
| **Khai báo mảng**    | `int[] arr = {1, 2, 3};`                                  | `let arr = [1, 2, 3];`              | `int[] arr = {1, 2, 3};`                  | `arr = [1, 2, 3]`                    | `arr := []int{1, 2, 3}`                                 | `$arr = [1, 2, 3];`                             |
| **Truy cập phần tử** | `arr[0]`                                                  | `arr[0]`                            | `arr[0]`                                  | `arr[0]`                             | `arr[0]`                                                | `$arr[0]`                                       |
| **Độ dài mảng**      | `arr.length`                                              | `arr.length`                        | `arr.Length`                              | `len(arr)`                           | `len(arr)`                                              | `count($arr)`                                   |
| **Lặp qua mảng**     | `for (int i : arr) {}`                                    | `arr.forEach(x => console.log(x));` | `foreach (int i in arr) {}`               | `for x in arr:`                      | `for _, x := range arr {}`                              | `foreach ($arr as $x) {}`                       |
| **Thêm phần tử**     | `arr = Arrays.copyOf(arr, arr.length + 1);`               | `arr.push(4);`                      | `arr = arr.Append(4).ToArray();`          | `arr.append(4)`                      | `arr = append(arr, 4)`                                  | `$arr[] = 4;`                                   |
| **Xóa phần tử**      | `arr = Arrays.stream(arr).filter(x -> x != 2).toArray();` | `arr.splice(1, 1);`                 | `arr = arr.Where(x => x != 2).ToArray();` | `arr.remove(2)`                      | Không hỗ trợ trực tiếp                                  | `$arr = array_filter($arr, fn($x) => $x != 2);` |
| **Sắp xếp mảng**     | `Arrays.sort(arr);`                                       | `arr.sort();`                       | `Array.Sort(arr);`                        | `arr.sort()`                         | `sort.Ints(arr)`                                        | `sort($arr);`                                   |
| **Tìm phần tử**      | `Arrays.asList(arr).contains(2)`                          | `arr.includes(2)`                   | `arr.Contains(2)`                         | `2 in arr`                           | `slices.Contains(arr, 2)`                               | `in_array(2, $arr);`                            |
| **Lọc mảng**         | `Arrays.stream(arr).filter(x -> x > 2).toArray();`        | `arr.filter(x => x > 2);`           | `arr.Where(x => x > 2).ToArray();`        | `list(filter(lambda x: x > 2, arr))` | `slices.Filter(arr, func(x int) bool { return x > 2 })` | `array_filter($arr, fn($x) => $x > 2);`         |

**Chú thích**
- **Khai báo mảng**: Cách tạo một mảng trong từng ngôn ngữ.
- **Truy cập phần tử**: Lấy giá trị phần tử tại một vị trí cụ thể.
- **Độ dài mảng**: Số phần tử trong mảng.
- **Lặp qua mảng**: Duyệt qua từng phần tử trong mảng.
- **Thêm phần tử**: Chèn một phần tử mới vào mảng.
- **Xóa phần tử**: Loại bỏ một phần tử khỏi mảng.
- **Sắp xếp mảng**: Sắp xếp các phần tử theo thứ tự tăng dần.
- **Tìm phần tử**: Kiểm tra xem một phần tử có tồn tại trong mảng hay không.
- **Lọc mảng**: Lấy các phần tử thỏa mãn điều kiện cụ thể.

[Lên đầu](#bảng-nội-dung)

---

# 11. Xử lý danh sách (List Handling)

| **Hạng mục**           | **Java**                                  | **JavaScript**                       | **C#**                              | **Python**       | **Go**                      | **PHP**                    |
|------------------------|-------------------------------------------|--------------------------------------|-------------------------------------|------------------|-----------------------------|----------------------------|
| **Khai báo danh sách** | `List<Integer> list = new ArrayList<>();` | `let list = [];`                     | `List<int> list = new List<int>();` | `list = []`      | `list := []int{}`           | `$list = array();`         |
| **Thêm phần tử**       | `list.add(1);`                            | `list.push(1);`                      | `list.Add(1);`                      | `list.append(1)` | `list = append(list, 1)`    | `$list[] = 1;`             |
| **Xóa phần tử**        | `list.remove(1);`                         | `list.splice(1, 1);`                 | `list.Remove(1);`                   | `list.remove(1)` | Không hỗ trợ trực tiếp      | `unset($list[1]);`         |
| **Lấy phần tử**        | `list.get(0);`                            | `list[0];`                           | `list[0];`                          | `list[0]`        | `list[0]`                   | `$list[0];`                |
| **Độ dài danh sách**   | `list.size();`                            | `list.length;`                       | `list.Count;`                       | `len(list)`      | `len(list)`                 | `count($list);`            |
| **Lặp qua danh sách**  | `for (int i : list) {}`                   | `list.forEach(x => console.log(x));` | `foreach (int i in list) {}`        | `for x in list:` | `for _, x := range list {}` | `foreach ($list as $x) {}` |

[Lên đầu](#bảng-nội-dung)

---

# 12. Xử lý tập hợp (Set Handling)

| **Hạng mục**         | **Java**                              | **JavaScript**         | **C#**                                   | **Python**       | **Go**                      | **PHP**                               |
|----------------------|---------------------------------------|------------------------|------------------------------------------|------------------|-----------------------------|---------------------------------------|
| **Khai báo tập hợp** | `Set<Integer> set = new HashSet<>();` | `let set = new Set();` | `HashSet<int> set = new HashSet<int>();` | `set = set()`    | `set := map[int]struct{}{}` | `$set = [];`                          |
| **Thêm phần tử**     | `set.add(1);`                         | `set.add(1);`          | `set.Add(1);`                            | `set.add(1)`     | `set[1] = struct{}{}`       | `$set[] = 1;`                         |
| **Xóa phần tử**      | `set.remove(1);`                      | `set.delete(1);`       | `set.Remove(1);`                         | `set.discard(1)` | `delete(set, 1)`            | `unset($set[array_search(1, $set)]);` |
| **Kiểm tra phần tử** | `set.contains(1);`                    | `set.has(1);`          | `set.Contains(1);`                       | `1 in set`       | `_, exists := set[1]`       | `in_array(1, $set);`                  |

[Lên đầu](#bảng-nội-dung)

---

# 13. Xử lý ánh xạ (Dictionary/Map Handling)

| **Hạng mục**        | **Java**                                      | **JavaScript**         | **C#**                                                         | **Python**       | **Go**                        | **PHP**               |
|---------------------|-----------------------------------------------|------------------------|----------------------------------------------------------------|------------------|-------------------------------|-----------------------|
| **Khai báo ánh xạ** | `Map<String, Integer> map = new HashMap<>();` | `let map = new Map();` | `Dictionary<string, int> map = new Dictionary<string, int>();` | `map = {}`       | `map := make(map[string]int)` | `$map = array();`     |
| **Thêm phần tử**    | `map.put("key", 1);`                          | `map.set("key", 1);`   | `map["key"] = 1;`                                              | `map["key"] = 1` | `map["key"] = 1`              | `$map["key"] = 1;`    |
| **Xóa phần tử**     | `map.remove("key");`                          | `map.delete("key");`   | `map.Remove("key");`                                           | `del map["key"]` | `delete(map, "key")`          | `unset($map["key"]);` |
| **Lấy giá trị**     | `map.get("key");`                             | `map.get("key");`      | `map["key"];`                                                  | `map.get("key")` | `value, exists := map["key"]` | `$map["key"];`        |

[Lên đầu](#bảng-nội-dung)

---

# 14. Xử lý JSON (JSON Handling)

| **Hạng mục**                 | **Java**                                   | **JavaScript**         | **C#**                                         | **Python**        | **Go**                              | **PHP**                              |
|------------------------------|--------------------------------------------|------------------------|------------------------------------------------|-------------------|-------------------------------------|--------------------------------------|
| **Chuyển object thành JSON** | `new Gson().toJson(obj);`                  | `JSON.stringify(obj);` | `JsonConvert.SerializeObject(obj);`            | `json.dumps(obj)` | `json.Marshal(obj)`                 | `json_encode($obj);`                 |
| **Chuyển JSON thành object** | `new Gson().fromJson(str, MyClass.class);` | `JSON.parse(str);`     | `JsonConvert.DeserializeObject<MyClass>(str);` | `json.loads(str)` | `json.Unmarshal([]byte(str), &obj)` | `$obj = json_decode($str, true);`    |

[Lên đầu](#bảng-nội-dung)

# 15. Xử lý tệp (File Handling)

| **Hạng mục** | **Java**                                      | **JavaScript**                                      | **C#**                                                       | **Python**                     | **Go**                                                       | **PHP**                                          |
|--------------|-----------------------------------------------|-----------------------------------------------------|--------------------------------------------------------------|--------------------------------|--------------------------------------------------------------|--------------------------------------------------|
| **Mở tệp**   | `File file = new File("file.txt");`           | `let fs = require('fs'); fs.open('file.txt', 'r');` | `FileStream fs = new FileStream("file.txt", FileMode.Open);` | `file = open("file.txt", "r")` | `file, err := os.Open("file.txt")`                           | `$file = fopen("file.txt", "r");`                |
| **Đọc tệp**  | `Scanner sc = new Scanner(file);`             | `fs.readFileSync('file.txt', 'utf8');`              | `StreamReader sr = new StreamReader(fs);`                    | `content = file.read()`        | `data, err := ioutil.ReadFile("file.txt")`                   | `$content = fread($file, filesize("file.txt"));` |
| **Ghi tệp**  | `FileWriter fw = new FileWriter("file.txt");` | `fs.writeFileSync('file.txt', 'Hello');`            | `StreamWriter sw = new StreamWriter(fs);`                    | `file.write("Hello")`          | `err := ioutil.WriteFile("file.txt", []byte("Hello"), 0644)` | `fwrite($file, "Hello");`                        |

[Lên đầu](#bảng-nội-dung)

---

# 16. Xử lý đồng thời (Concurrency Handling)

| **Hạng mục**                    | **Java**                           | **JavaScript**             | **C#**                             | **Python**                              | **Go**                | **PHP**                |
|---------------------------------|------------------------------------|----------------------------|------------------------------------|-----------------------------------------|-----------------------|------------------------|
| **Tạo luồng (Threading)**       | `new Thread(() -> {...}).start();` | `new Worker("script.js");` | `new Thread(() => {...}).Start();` | `threading.Thread(target=func).start()` | `go func() { ... }()` | `pcntl_fork();`        |
| **Chờ luồng kết thúc**          | `thread.join();`                   | `worker.terminate();`      | `thread.Join();`                   | `thread.join()`                         | `wg.Wait()`           | `pcntl_wait($status);` |
| **Tạo Goroutine (Go-specific)** | Không có                           | Không có                   | Không có                           | Không có                                | `go func() { ... }()` | Không có               |

[Lên đầu](#bảng-nội-dung)