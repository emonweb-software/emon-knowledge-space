# Cheatsheet & Hướng dẫn phát triển WordPress

[![English](https://img.shields.io/badge/language-English-blue.svg)](wordpress.md)

---

## Bảng nội dung

<!-- TOC -->
* [1. Giới thiệu](#1-giới-thiệu)
  * [1.1. Tổng quan](#11-tổng-quan)
  * [1.2. Các thành phần chính](#12-các-thành-phần-chính)
* [2. Thiết lập môi trường phát triển](#2-thiết-lập-môi-trường-phát-triển)
  * [2.1. Thiết lập môi trường cục bộ](#21-thiết-lập-môi-trường-cục-bộ)
  * [2.2. Cài đặt WordPress](#22-cài-đặt-wordpress)
  * [2.3. Các công cụ thiết yếu](#23-các-công-cụ-thiết-yếu)
* [3. Kiến trúc WordPress & Cấu trúc file](#3-kiến-trúc-wordpress--cấu-trúc-file)
  * [3.1. Cấu trúc thư mục](#31-cấu-trúc-thư-mục)
  * [3.2. Mã nguồn tùy chỉnh vs. Mã nguồn cốt lõi](#32-mã-nguồn-tùy-chỉnh-vs-mã-nguồn-cốt-lõi)
* [4. API WordPress & Hệ thống Hook](#4-api-wordpress--hệ-thống-hook)
  * [4.1. Actions & Filters (Hooks)](#41-actions--filters-hooks)
  * [4.2. Các API khác](#42-các-api-khác)
* [5. Chuẩn mã & Best practices](#5-chuẩn-mã--best-practices)
  * [5.1. Tuân thủ Coding Standards](#51-tuân-thủ-coding-standards)
  * [5.2. Quy ước đặt tên](#52-quy-ước-đặt-tên)
  * [5.3. Bảo mật](#53-bảo-mật)
  * [5.4. Internationalization (i18n) & Localization (l10n)](#54-internationalization-i18n--localization-l10n)
* [6. Debug, hiệu năng & Tối ưu hóa](#6-debug-hiệu-năng--tối-ưu-hóa)
  * [6.1. Debugging](#61-debugging)
  * [6.2. Tối ưu hóa hiệu năng](#62-tối-ưu-hóa-hiệu-năng)
  * [6.3. Công cụ Profiling](#63-công-cụ-profiling)
* [7. Triển khai & Bảo trì](#7-triển-khai--bảo-trì)
  * [7.1. Quản lý phiên bản](#71-quản-lý-phiên-bản)
  * [7.2. Môi trường Staging](#72-môi-trường-staging)
  * [7.3. Sao lưu](#73-sao-lưu)
  * [7.4. Cập nhật & Bảo mật](#74-cập-nhật--bảo-mật)
  * [7.5. Tài liệu & Ghi chú mã nguồn](#75-tài-liệu--ghi-chú-mã-nguồn)
* [8. Công cụ & Tài nguyên tham khảo](#8-công-cụ--tài-nguyên-tham-khảo)
  * [8.1. Tài liệu chính thức](#81-tài-liệu-chính-thức)
  * [8.2. WP-CLI](#82-wp-cli)
  * [8.3. Công cụ hỗ trợ](#83-công-cụ-hỗ-trợ)
  * [8.4. Cộng đồng](#84-cộng-đồng)
<!-- TOC -->

---

## 1. Giới thiệu

### 1.1. Tổng quan

WordPress là một hệ thống quản trị nội dung (CMS) mạnh mẽ, cho phép các nhà phát triển tạo ra các website động bằng cách sử dụng theme, plugin và mã tùy chỉnh. Tài liệu này cung cấp các best practices và hướng dẫn cần thiết cho việc phát triển trên WordPress.

### 1.2. Các thành phần chính

- **Core:** Các tập tin cốt lõi của WordPress, không được chỉnh sửa.
- **Themes:** Kiểm soát giao diện và bố cục trang web.
- **Plugins:** Mở rộng các chức năng của WordPress.
- **Child Themes:** Cho phép tùy biến an toàn bằng cách kế thừa từ theme cha mà không làm thay đổi mã nguồn gốc.

[Lên đầu](#bảng-nội-dung)

---

## 2. Thiết lập môi trường phát triển

### 2.1. Thiết lập môi trường cục bộ
Sử dụng các công cụ như [LocalWP](https://localwp.com/), [XAMPP](https://www.apachefriends.org/), [MAMP](https://www.mamp.info/) hoặc Docker để tạo máy chủ cục bộ.
### 2.2. Cài đặt WordPress
- Tải WordPress từ [WordPress.org](https://wordpress.org/download/).
- Làm theo các bước hướng dẫn để cài đặt website phát triển cục bộ.
### 2.3. Các công cụ thiết yếu
- **WP-CLI:** Giao diện dòng lệnh để quản lý WordPress.
- **Quản lý phiên bản:** Sử dụng Git để quản lý mã nguồn.
- **IDE/Editor:** Các công cụ như VS Code hoặc PhpStorm, có cấu hình hỗ trợ chuẩn coding của WordPress.

[Lên đầu](#bảng-nội-dung)

---

## 3. Kiến trúc WordPress & Cấu trúc file

### 3.1. Cấu trúc thư mục

- **wp-admin:** Chứa các tập tin cho trang quản trị.
- **wp-includes:** Các thư viện và hàm cốt lõi.
- **wp-content:** Nơi chứa theme, plugin và file tải lên.
  - `themes/`: Các giao diện (theme) hiển thị website.
  - `plugins/`: Các plugin tùy chỉnh và bên thứ ba.
  - `uploads/`: File truyền tải từ trang quản trị.

### 3.2. Mã nguồn tùy chỉnh vs. Mã nguồn cốt lõi

Luôn đặt các tùy chỉnh của bạn trong theme (ưu tiên sử dụng child theme) hoặc plugin để tránh xung đột khi cập nhật core.

[Lên đầu](#bảng-nội-dung)

---

## 4. API WordPress & Hệ thống Hook

### 4.1. Actions & Filters (Hooks)

Hooks cho phép bạn can thiệp vào các điểm nhất định của quá trình thực thi WordPress.

- **Ví dụ về Actions:**
  ```php
  add_action('init', 'my_custom_init');
    
  function my_custom_init() {
      // Code chạy trong quá trình khởi tạo WordPress
  }
  ```
- **Ví dụ về Filters:**
  ```php
  add_filter('the_content', 'my_custom_content_filter');
    
  function my_custom_content_filter($content) {
      return $content . '<p>Thêm nội dung bổ sung.</p>';
  }
  ```

### 4.2. Các API khác

- **Options API:** Lưu trữ và truy xuất các thiết lập cấu hình.
  ```php
  update_option('my_option', 'giá trị');
  $value = get_option('my_option', 'mặc định');
  ```
- **Transients API:** Lưu trữ tạm thời (cache) dữ liệu với thời gian sống xác định.
  ```php
  set_transient('my_transient', $data, 12 * HOUR_IN_SECONDS);
  $data = get_transient('my_transient');
  ```
- **HTTP API:** Tương tác với các API bên ngoài.
  ```php
  $response = wp_remote_get('https://api.example.com/data');
  if (is_wp_error($response)) {
      // Xử lý lỗi
  } else {
      $body = wp_remote_retrieve_body($response);
  }
  ```
- **Database API ($wpdb):** Thực hiện truy vấn cơ sở dữ liệu một cách an toàn.
  ```php
  global $wpdb;
  $table = $wpdb->prefix . 'mytable';
  $id = intval($_GET['id']);
  $query = $wpdb->prepare("SELECT * FROM $table WHERE id = %d", $id);
  $result = $wpdb->get_results($query);
  ```
- **REST API:** Tạo các endpoint tùy chỉnh để tương tác với dữ liệu của WordPress.
  ```php
  add_action('rest_api_init', function () {
      register_rest_route('myplugin/v1', '/data', [
          'methods'  => 'GET',
          'callback' => 'myplugin_get_data',
      ]);
  });
    
  function myplugin_get_data() {
      return ['data' => 'Giá trị trả về'];
  }
  ```

[Lên đầu](#bảng-nội-dung)

---

## 5. Chuẩn mã & Best practices

### 5.1. Tuân thủ Coding Standards

Tham khảo [WordPress Coding Standards](https://developer.wordpress.org/coding-standards/wordpress-coding-standards/) cho PHP, HTML, CSS và JavaScript.

### 5.2. Quy ước đặt tên

Sử dụng tiền tố (ví dụ: `myplugin_`) cho các hàm, lớp, và biến. Sử dụng namespace cho mã hướng đối tượng khi cần thiết.

### 5.3. Bảo mật

- **Sanitization:** Lọc dữ liệu đầu vào bằng các hàm như `sanitize_text_field()`, `sanitize_email()`,…
- **Validation:** Kiểm tra dữ liệu theo định dạng mong muốn.
- **Escaping:** Sử dụng `esc_html()`, `esc_url()`, `esc_attr()` khi xuất dữ liệu ra trình duyệt.
- **Nonces:** Bảo vệ form và URL tránh tấn công CSRF.
  ```php
  $nonce = wp_create_nonce('my_nonce');
  if ( ! isset($_REQUEST['_wpnonce']) || ! wp_verify_nonce($_REQUEST['_wpnonce'], 'my_nonce') ) {
      wp_die('Nonce không hợp lệ!');
  }
  ```

### 5.4. Internationalization (i18n) & Localization (l10n)
- Gói tất cả chuỗi hiển thị cho người dùng bằng các hàm dịch như `__()`, `_e()`, v.v.
- Load text domain cho theme/plugin:
  ```php
  function mytheme_load_textdomain() {
      load_theme_textdomain('mytheme', get_template_directory() . '/languages');
  }
  add_action('after_setup_theme', 'mytheme_load_textdomain');
  ```

[Lên đầu](#bảng-nội-dung)

---

## 6. Debug, hiệu năng & Tối ưu hóa

### 6.1. Debugging

Kích hoạt chế độ debug trong tệp `wp-config.php`:
```php
define('WP_DEBUG', true);
define('WP_DEBUG_LOG', true);
define('WP_DEBUG_DISPLAY', false);
```
Sử dụng các plugin như [Query Monitor](https://wordpress.org/plugins/query-monitor/) để theo dõi lỗi và hiệu năng.

### 6.2. Tối ưu hóa hiệu năng

- **Caching:** Áp dụng chiến lược cache (Transients API, object cache).
- **Tối ưu truy vấn:** Luôn sử dụng `$wpdb->prepare()` cho các truy vấn cơ sở dữ liệu.
- **Tối ưu tài nguyên:** Minify và kết hợp các tệp CSS/JS.

### 6.3. Công cụ Profiling

Sử dụng Xdebug và các công cụ profiling khác để phát hiện nút thắt hiệu năng.

[Lên đầu](#bảng-nội-dung)

---

## 7. Triển khai & Bảo trì

### 7.1. Quản lý phiên bản

Sử dụng Git để quản lý mã nguồn và theo dõi lịch sử thay đổi.

### 7.2. Môi trường Staging

Luôn thử nghiệm các thay đổi trên môi trường staging trước khi triển khai lên production.

### 7.3. Sao lưu

Thực hiện sao lưu định kỳ cho cơ sở dữ liệu và các tập tin.

### 7.4. Cập nhật & Bảo mật

Theo dõi và cập nhật WordPress, theme, plugin cũng như vá lỗi bảo mật kịp thời.

### 7.5. Tài liệu & Ghi chú mã nguồn

Ghi chú rõ ràng bằng DocBlocks (PHPDoc) và các comment trong mã để đảm bảo dễ bảo trì.

[Lên đầu](#bảng-nội-dung)

---

## 8. Công cụ & Tài nguyên tham khảo

### 8.1. Tài liệu chính thức

- [WordPress Developer Handbook](https://developer.wordpress.org/)
- [WordPress Codex](https://codex.wordpress.org/)
- [Plugin Developer Handbook](https://developer.wordpress.org/plugins/)
- [Theme Developer Handbook](https://developer.wordpress.org/themes/)

### 8.2. WP-CLI

[Tài liệu WP-CLI](https://wp-cli.org/)

### 8.3. Công cụ hỗ trợ

- PHP CodeSniffer với WordPress Coding Standards.
- Các plugin debug như Query Monitor.

### 8.4. Cộng đồng

Diễn đàn, blog, meetup, và các kênh Slack của cộng đồng WordPress.

[Lên đầu](#bảng-nội-dung)