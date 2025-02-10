# Cheatsheet & Hướng dẫn phát triển WordPress Plugin

[![English](https://img.shields.io/badge/language-English-blue.svg)](wordpress-plugin.md)

Tài liệu này tổng hợp các best practices khi phát triển plugin cho wordpress, tập trung vào giao diện quản trị và các tính năng mở rộng (ajax, rest api, shortcode, custom post type). nội dung dưới đây chủ yếu nhằm hỗ trợ các phần chưa được đề cập chi tiết trong tài liệu wordpress chính thức.

---

## 1. Tổ chức code & Cấu trúc thư mục

### 1.1. Plugin header

File chính (ví dụ: `my-awesome-plugin.php`) chứa header comment
  ```
  <?php
    /*
    Plugin Name: My Awesome Plugin
    Plugin URI: https://example.com/my-awesome-plugin
    Description: Mô tả ngắn gọn về plugin.
    Version: 1.0.0
    Author: Your Name
    Author URI: https://example.com
    License: GPL2
    Text Domain: my-awesome-plugin
  */
  ```

### 1.2. Cấu trúc thư mục

```
my-awesome-plugin/
├── my-awesome-plugin.php    // file chính của plugin
├── includes/                // các file bổ trợ (class, function,…)
├── assets/                  // css, js, images
│   ├── css/
│   ├── js/
│   └── images/
├── languages/               // file dịch (i18n)
└── readme.txt               // hướng dẫn sử dụng
```

### 1.3. Tổ chức code
- Sử dụng tiền tố (ví dụ: `myplugin_`) hoặc namespace (cho oops) để tránh xung đột
- Chia nhỏ code thành các module riêng biệt: logic xử lý, giao diện, dữ liệu
- Sử dụng docblocks và comment rõ ràng nhằm hỗ trợ bảo trì

## 2. Phát triển giao diện quản trị (Admin UI)

### 2.1. Tạo menu & Trang quản trị

- **Tạo menu chính & submenu:**  
  sử dụng `add_menu_page()` và `add_submenu_page()` để thêm mục vào trang quản trị
  ```php
  function myplugin_add_admin_menu() {
      add_menu_page(
          __('cài đặt my plugin', 'my-awesome-plugin'), // tiêu đề trang
          __('my plugin', 'my-awesome-plugin'),          // tên hiển thị
          'manage_options',
          'myplugin_settings',
          'myplugin_settings_page',
          'dashicons-admin-generic',
          90
      );
  
      add_submenu_page(
          'myplugin_settings',
          __('cài đặt nâng cao', 'my-awesome-plugin'),
          __('nâng cao', 'my-awesome-plugin'),
          'manage_options',
          'myplugin_advanced',
          'myplugin_advanced_page'
      );
  }
  add_action('admin_menu', 'myplugin_add_admin_menu');
  ```

- **Trang cài đặt (settings page):**  
  xử lý lưu dữ liệu qua form, sử dụng nonces để bảo mật
  ```php
  function myplugin_settings_page() {
      if ( ! current_user_can('manage_options') ) {
          wp_die(__('bạn không có quyền truy cập chức năng này.', 'my-awesome-plugin'));
      }
  
      if ( isset($_POST['myplugin_settings_submit']) && check_admin_referer('myplugin_settings_action', 'myplugin_settings_nonce') ) {
          $option_value = isset($_POST['myplugin_option']) ? sanitize_text_field($_POST['myplugin_option']) : '';
          update_option('myplugin_option', $option_value);
          echo '<div class="updated"><p>' . esc_html__('đã lưu cài đặt.', 'my-awesome-plugin') . '</p></div>';
      }
  
      $option_value = get_option('myplugin_option', '');
      ?>
      <div class="wrap">
          <h1><?php esc_html_e('cài đặt my plugin', 'my-awesome-plugin'); ?></h1>
          <form method="post" action="">
              <?php wp_nonce_field('myplugin_settings_action', 'myplugin_settings_nonce'); ?>
              <table class="form-table">
                  <tr>
                      <th scope="row"><?php esc_html_e('nhãn tùy chọn', 'my-awesome-plugin'); ?></th>
                      <td>
                          <input type="text" name="myplugin_option" value="<?php echo esc_attr($option_value); ?>" class="regular-text" />
                          <p class="description"><?php esc_html_e('mô tả cho tùy chọn này.', 'my-awesome-plugin'); ?></p>
                      </td>
                  </tr>
              </table>
              <?php submit_button(__('lưu cài đặt', 'my-awesome-plugin'), 'primary', 'myplugin_settings_submit'); ?>
          </form>
      </div>
      <?php
  }
  ```

- **Trang cài đặt nâng cao (nếu cần):**
  ```php
  function myplugin_advanced_page() {
      if ( ! current_user_can('manage_options') ) {
          wp_die(__('bạn không có quyền truy cập chức năng này.', 'my-awesome-plugin'));
      }
      ?>
      <div class="wrap">
          <h1><?php esc_html_e('cài đặt nâng cao', 'my-awesome-plugin'); ?></h1>
          <!-- nội dung cài đặt nâng cao -->
      </div>
      <?php
  }
  ```

### 2.2. Dashboard Widget

- **Thêm widget thống kê vào dashboard:**
  ```php
  function myplugin_add_dashboard_widget() {
      wp_add_dashboard_widget(
          'myplugin_dashboard_widget', // slug widget
          __('thống kê my plugin', 'my-awesome-plugin'),
          'myplugin_dashboard_widget_display'
      );
  }
  add_action('wp_dashboard_setup', 'myplugin_add_dashboard_widget');
  
  function myplugin_dashboard_widget_display() {
      echo '<p>' . esc_html__('tổng số người dùng: 1234', 'my-awesome-plugin') . '</p>';
      echo '<p>' . esc_html__('tổng số bài viết liên quan: 567', 'my-awesome-plugin') . '</p>';
  }
  ```

### 2.3. Thông báo quản trị (Admin Notices)

- **hiển thị thông báo trong trang quản trị:**
  ```php
  function myplugin_admin_notice() {
      ?>
      <div class="notice notice-success is-dismissible">
          <p><?php esc_html_e('my plugin đã được cập nhật thành công!', 'my-awesome-plugin'); ?></p>
      </div>
      <?php
  }
  add_action('admin_notices', 'myplugin_admin_notice');
  ```

---

## 3. Các tính năng mở rộng

### 3.1. Xử lý AJAX

- **Đăng ký AJAX Action:**  
  xử lý cả cho người dùng đã đăng nhập và chưa đăng nhập
  ```php
  function myplugin_ajax_handler() {
      check_ajax_referer('myplugin_ajax_nonce', 'security');
  
      $response = array(
          'message' => __('đây là phản hồi ajax', 'my-awesome-plugin')
      );
  
      wp_send_json_success($response);
  }
  add_action('wp_ajax_myplugin_action', 'myplugin_ajax_handler');
  add_action('wp_ajax_nopriv_myplugin_action', 'myplugin_ajax_handler');
  ```

- **Gửi AJAX request (ví dụ với jQuery):**
  ```js
  jQuery(document).ready(function($) {
      $.ajax({
          url: myplugin_ajax_object.ajax_url,
          type: 'POST',
          data: {
              action: 'myplugin_action',
              security: myplugin_ajax_object.ajax_nonce
          },
          success: function(response) {
              if ( response.success ) {
                  console.log(response.data.message);
              }
          }
      });
  });
  ```

- **Localize script để truyền biến AJAX:**
  ```php
  wp_localize_script('myplugin-script', 'myplugin_ajax_object', array(
      'ajax_url'   => admin_url('admin-ajax.php'),
      'ajax_nonce' => wp_create_nonce('myplugin_ajax_nonce')
  ));
  ```

### 3.2. Tạo rest api endpoint

- **Đăng ký endpoint trong rest api:**
  ```php
  function myplugin_register_rest_routes() {
      register_rest_route('myplugin/v1', '/data', array(
          'methods'             => 'GET',
          'callback'            => 'myplugin_rest_callback',
          'permission_callback' => '__return_true',
      ));
  }
  add_action('rest_api_init', 'myplugin_register_rest_routes');
  
  function myplugin_rest_callback($request) {
      return new WP_REST_Response(array(
          'data' => __('xin chào từ rest api', 'my-awesome-plugin')
      ), 200);
  }
  ```

### 3.3. Tạo shortcode

- **Đăng ký shortcode:**
  ```php
  function myplugin_shortcode_handler($atts, $content = null) {
      $atts = shortcode_atts(array(
          'title' => __('tiêu đề mặc định', 'my-awesome-plugin'),
      ), $atts, 'myplugin_shortcode');
  
      return '<div class="myplugin-shortcode"><h2>' . esc_html($atts['title']) . '</h2>' . do_shortcode($content) . '</div>';
  }
  add_shortcode('myplugin_shortcode', 'myplugin_shortcode_handler');
  ```

### 3.4. Tạo custom post type

- **Đăng ký custom post type:**
  ```php
  function myplugin_register_post_type() {
      $labels = array(
          'name'               => __('sách', 'my-awesome-plugin'),
          'singular_name'      => __('sách', 'my-awesome-plugin'),
          'add_new'            => __('thêm mới', 'my-awesome-plugin'),
          'add_new_item'       => __('thêm sách mới', 'my-awesome-plugin'),
          'edit_item'          => __('chỉnh sửa sách', 'my-awesome-plugin'),
          'new_item'           => __('sách mới', 'my-awesome-plugin'),
          'all_items'          => __('tất cả sách', 'my-awesome-plugin'),
          'view_item'          => __('xem sách', 'my-awesome-plugin'),
          'search_items'       => __('tìm kiếm sách', 'my-awesome-plugin'),
          'not_found'          => __('không tìm thấy sách', 'my-awesome-plugin'),
          'not_found_in_trash' => __('không tìm thấy sách trong thùng rác', 'my-awesome-plugin'),
          'menu_name'          => __('sách', 'my-awesome-plugin'),
      );
  
      $args = array(
          'labels'             => $labels,
          'public'             => true,
          'has_archive'        => true,
          'rewrite'            => array('slug' => 'sach'),
          'supports'           => array('title', 'editor', 'thumbnail', 'excerpt'),
          'show_in_rest'       => true, // hỗ trợ cho block editor (gutenberg)
      );
  
      register_post_type('myplugin_book', $args);
  }
  add_action('init', 'myplugin_register_post_type');
  ```