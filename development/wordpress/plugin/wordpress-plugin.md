# Wordpress Plugin Cheatsheet & Best Practices

[![Vietnamese](https://img.shields.io/badge/language-Vietnamese-blue.svg)](wordpress-plugin.vi.md)

This document summarizes best practices when developing plugins for wordpress, focusing on the admin interface and extended features (ajax, rest api, shortcodes, custom post types). the content below is mainly aimed at supporting areas that are not covered in detail in the official wordpress documentation.

---

## 1. Organizing code & Project structure

### 1.1. Plugin header

Main file (e.g., `my-awesome-plugin.php`) contains the plugin header comment
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

### 1.2. Folder structure

```
my-awesome-plugin/
├── my-awesome-plugin.php    // main plugin file
├── includes/                // supplementary PHP files (classes, functions,…)
├── assets/                  // css, js, images
│   ├── css/
│   ├── js/
│   └── images/
├── languages/               // translation files (i18n)
└── readme.txt               // usage instructions
```

### 1.3. Code organization

- Use a unique prefix (e.g., `myplugin_`) or namespaces (for OOP) to avoid conflicts.
- Divide your code into separate modules: logic, UI, and data handling.
- Use docblocks and clear comments to aid maintenance.

### 2. Developing the Admin UI

#### 2.1. Creating admin menu & Settings page

- **Adding main menu & submenu:** Use `add_menu_page()` and `add_submenu_page()` to add items in the wp-admin.
  ```php
  function myplugin_add_admin_menu() {
      add_menu_page(
          __('my plugin settings', 'my-awesome-plugin'), // page title
          __('my plugin', 'my-awesome-plugin'),          // menu title
          'manage_options',
          'myplugin_settings',
          'myplugin_settings_page',
          'dashicons-admin-generic',
          90
      );
  
      add_submenu_page(
          'myplugin_settings',
          __('advanced settings', 'my-awesome-plugin'),
          __('advanced', 'my-awesome-plugin'),
          'manage_options',
          'myplugin_advanced',
          'myplugin_advanced_page'
      );
  }
  add_action('admin_menu', 'myplugin_add_admin_menu');
  ```

- **Settings page:** Process form submissions securely using nonces.
  ```php
  function myplugin_settings_page() {
      if ( ! current_user_can('manage_options') ) {
          wp_die(__('you do not have sufficient permissions to access this page.', 'my-awesome-plugin'));
      }
  
      if ( isset($_POST['myplugin_settings_submit']) && check_admin_referer('myplugin_settings_action', 'myplugin_settings_nonce') ) {
          $option_value = isset($_POST['myplugin_option']) ? sanitize_text_field($_POST['myplugin_option']) : '';
          update_option('myplugin_option', $option_value);
          echo '<div class="updated"><p>' . esc_html__('settings saved.', 'my-awesome-plugin') . '</p></div>';
      }
  
      $option_value = get_option('myplugin_option', '');
      ?>
      <div class="wrap">
          <h1><?php esc_html_e('my plugin settings', 'my-awesome-plugin'); ?></h1>
          <form method="post" action="">
              <?php wp_nonce_field('myplugin_settings_action', 'myplugin_settings_nonce'); ?>
              <table class="form-table">
                  <tr>
                      <th scope="row"><?php esc_html_e('option label', 'my-awesome-plugin'); ?></th>
                      <td>
                          <input type="text" name="myplugin_option" value="<?php echo esc_attr($option_value); ?>" class="regular-text" />
                          <p class="description"><?php esc_html_e('description for this option.', 'my-awesome-plugin'); ?></p>
                      </td>
                  </tr>
              </table>
              <?php submit_button(__('save settings', 'my-awesome-plugin'), 'primary', 'myplugin_settings_submit'); ?>
          </form>
      </div>
      <?php
  }
  ```

- **Advanced settings page (if needed):**
  ```php
  function myplugin_advanced_page() {
      if ( ! current_user_can('manage_options') ) {
          wp_die(__('you do not have sufficient permissions to access this page.', 'my-awesome-plugin'));
      }
      ?>
      <div class="wrap">
          <h1><?php esc_html_e('advanced settings', 'my-awesome-plugin'); ?></h1>
          <!-- advanced settings content -->
      </div>
      <?php
  }
  ```

#### 2.2. Dashboard Widget

- **Adding a dashboard widget:**
  ```php
  function myplugin_add_dashboard_widget() {
      wp_add_dashboard_widget(
          'myplugin_dashboard_widget', // widget slug
          __('my plugin statistics', 'my-awesome-plugin'),
          'myplugin_dashboard_widget_display'
      );
  }
  add_action('wp_dashboard_setup', 'myplugin_add_dashboard_widget');
  
  function myplugin_dashboard_widget_display() {
      echo '<p>' . esc_html__('total users: 1234', 'my-awesome-plugin') . '</p>';
      echo '<p>' . esc_html__('total related posts: 567', 'my-awesome-plugin') . '</p>';
  }
  ```

#### 2.3. Admin Notices

- **Displaying admin notices:**
  ```php
  function myplugin_admin_notice() {
      ?>
      <div class="notice notice-success is-dismissible">
          <p><?php esc_html_e('my plugin has been updated successfully!', 'my-awesome-plugin'); ?></p>
      </div>
      <?php
  }
  add_action('admin_notices', 'myplugin_admin_notice');
  ```

---

## 3. Extended features

### 3.1. AJAX handling

- **Register ajax action:**  Handle for both logged-in and not logged-in users.
  ```php
  function myplugin_ajax_handler() {
      check_ajax_referer('myplugin_ajax_nonce', 'security');
  
      $response = array(
          'message' => __('this is an ajax response', 'my-awesome-plugin')
      );
  
      wp_send_json_success($response);
  }
  add_action('wp_ajax_myplugin_action', 'myplugin_ajax_handler');
  add_action('wp_ajax_nopriv_myplugin_action', 'myplugin_ajax_handler');
  ```

- **Sending an ajax request (with jQuery):**
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

- **Localize script for ajax variables:**
  ```php
  wp_localize_script('myplugin-script', 'myplugin_ajax_object', array(
      'ajax_url'   => admin_url('admin-ajax.php'),
      'ajax_nonce' => wp_create_nonce('myplugin_ajax_nonce')
  ));
  ```

### 3.2. Rest api endpoint

- **Register a rest api endpoint:**
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
          'data' => __('hello from rest api', 'my-awesome-plugin')
      ), 200);
  }
  ```

### 3.3. Shortcode

- **Register a shortcode:**
  ```php
  function myplugin_shortcode_handler($atts, $content = null) {
      $atts = shortcode_atts(array(
          'title' => __('default title', 'my-awesome-plugin'),
      ), $atts, 'myplugin_shortcode');
  
      return '<div class="myplugin-shortcode"><h2>' . esc_html($atts['title']) . '</h2>' . do_shortcode($content) . '</div>';
  }
  add_shortcode('myplugin_shortcode', 'myplugin_shortcode_handler');
  ```

### 3.4. Custom post type

- **Register a custom post type:**
  ```php
  function myplugin_register_post_type() {
      $labels = array(
          'name'               => __('books', 'my-awesome-plugin'),
          'singular_name'      => __('book', 'my-awesome-plugin'),
          'add_new'            => __('add new', 'my-awesome-plugin'),
          'add_new_item'       => __('add new book', 'my-awesome-plugin'),
          'edit_item'          => __('edit book', 'my-awesome-plugin'),
          'new_item'           => __('new book', 'my-awesome-plugin'),
          'all_items'          => __('all books', 'my-awesome-plugin'),
          'view_item'          => __('view book', 'my-awesome-plugin'),
          'search_items'       => __('search books', 'my-awesome-plugin'),
          'not_found'          => __('no books found', 'my-awesome-plugin'),
          'not_found_in_trash' => __('no books found in trash', 'my-awesome-plugin'),
          'menu_name'          => __('books', 'my-awesome-plugin'),
      );
  
      $args = array(
          'labels'             => $labels,
          'public'             => true,
          'has_archive'        => true,
          'rewrite'            => array('slug' => 'books'),
          'supports'           => array('title', 'editor', 'thumbnail', 'excerpt'),
          'show_in_rest'       => true, // support Gutenberg
      );
  
      register_post_type('myplugin_book', $args);
  }
  add_action('init', 'myplugin_register_post_type');
  ```