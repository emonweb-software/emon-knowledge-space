# WordPress Development Cheatsheet & Guidelines

[![Vietnamese](https://img.shields.io/badge/language-Vietnamese-blue.svg)](wordpress.vi.md)

---

## Table of Contents

<!-- TOC -->
* [1. Introduction](#1-introduction)
  * [1.1. Overview](#11-overview)
  * [1.2. Key Components](#12-key-components)
* [2. Setting Up Your Development Environment](#2-setting-up-your-development-environment)
  * [2.1. Local Environment Setup](#21-local-environment-setup)
  * [2.2. Installation](#22-installation)
* [3. WordPress Architecture & File Structure](#3-wordpress-architecture--file-structure)
  * [3.1. Directory Structure:](#31-directory-structure)
  * [3.2. Custom vs. Core Code](#32-custom-vs-core-code)
* [4. WordPress API & Hook System](#4-wordpress-api--hook-system)
  * [4.1. Actions & Filters (Hooks)](#41-actions--filters-hooks)
  * [4.2. Other APIs](#42-other-apis)
* [5. Coding Standards & Best Practices](#5-coding-standards--best-practices)
  * [5.1. Coding Standards](#51-coding-standards)
  * [5.2. Naming Conventions](#52-naming-conventions)
  * [5.3. Security Practices](#53-security-practices)
  * [5.4. Internationalization (i18n) & Localization (l10n)](#54-internationalization-i18n--localization-l10n)
* [6. Debugging, Performance & Optimization](#6-debugging-performance--optimization)
  * [6.1. Debugging](#61-debugging)
  * [6.2. Performance Optimization](#62-performance-optimization)
  * [6.3. Profiling Tools](#63-profiling-tools)
  * [7. Deployment & Maintenance](#7-deployment--maintenance)
* [8. Tools & Resources](#8-tools--resources)
  * [8.1. Official Documentation](#81-official-documentation)
  * [8.2. WP-CLI](#82-wp-cli)
  * [8.3. Additional Tools](#83-additional-tools)
  * [8.4. Community Resources](#84-community-resources)
<!-- TOC -->

---

## 1. Introduction

### 1.1. Overview

WordPress is a powerful content management system (CMS) that enables developers to create dynamic websites using themes, plugins, and custom code. This guide provides best practices and essential guidelines for developing on WordPress.

### 1.2. Key Components

- **Core:** The WordPress core files that should never be modified.
- **Themes:** Control the front-end design and layout.
- **Plugins:** Extend WordPress functionalities.
- **Child Themes:** Safely customize a parent theme without altering its source code.

[To Top](#table-of-contents)

---

## 2. Setting Up Your Development Environment

### 2.1. Local Environment Setup
Use tools such as [LocalWP](https://localwp.com/), [XAMPP](https://www.apachefriends.org/), [MAMP](https://www.mamp.info/), or Docker to create a local server.

### 2.2. Installation

- Download WordPress from [WordPress.org](https://wordpress.org/download/). Follow the installation steps to set up your local development site.
- Essential Tools:
  - **WP-CLI:** Command-line interface for managing WordPress.
  - **Version Control:** Use Git for source code management.
  - **IDE/Editor:** Tools like VS Code or PhpStorm, configured with WordPress coding standards.

[To Top](#table-of-contents)

---

## 3. WordPress Architecture & File Structure

### 3.1. Directory Structure:
- **wp-admin:** Contains files for the admin dashboard.
- **wp-includes:** Core libraries and functions.
- **wp-content:** Holds themes, plugins, and uploads.
    - `themes/`: Your front-end themes.
    - `plugins/`: Custom and third-party plugins.
    - `uploads/`: Media files uploaded via the dashboard.

### 3.2. Custom vs. Core Code
  Always place your customizations in themes (preferably child themes) or plugins to avoid conflicts with core updates.

[To Top](#table-of-contents)

---

## 4. WordPress API & Hook System
### 4.1. Actions & Filters (Hooks)
Hooks allow you to interact with WordPress at specific points.
- **Actions Example:**
  ```php
  add_action('init', 'my_custom_init');
  
  function my_custom_init() {
      // Code to execute during initialization
  }
  ```
- **Filters Example:**
  ```php
  add_filter('the_content', 'my_custom_content_filter');
  
  function my_custom_content_filter($content) {
      return $content . '<p>Additional content appended.</p>';
  }
  ```
### 4.2. Other APIs
- **Options API:** For storing and retrieving configuration settings.
  ```php
  update_option('my_option', 'value');
  $value = get_option('my_option', 'default');
  ```
- **Transients API:** For caching data temporarily.
  ```php
  set_transient('my_transient', $data, 12 * HOUR_IN_SECONDS);
  $data = get_transient('my_transient');
  ```
- **HTTP API:** For external HTTP requests.
  ```php
  $response = wp_remote_get('https://api.example.com/data');
  if (is_wp_error($response)) {
      // Handle error
  } else {
      $body = wp_remote_retrieve_body($response);
  }
  ```
- **Database API ($wpdb):**
  ```php
  global $wpdb;
  $table = $wpdb->prefix . 'mytable';
  $id = intval($_GET['id']);
  $query = $wpdb->prepare("SELECT * FROM $table WHERE id = %d", $id);
  $result = $wpdb->get_results($query);
  ```
- **REST API:**
  ```php
  add_action('rest_api_init', function () {
      register_rest_route('myplugin/v1', '/data', [
          'methods'  => 'GET',
          'callback' => 'myplugin_get_data',
      ]);
  });
  
  function myplugin_get_data() {
      return ['data' => 'Returned value'];
  }
  ```

[To Top](#table-of-contents)

---

## 5. Coding Standards & Best Practices

### 5.1. Coding Standards

Follow the [WordPress Coding Standards](https://developer.wordpress.org/coding-standards/wordpress-coding-standards/) for PHP, HTML, CSS, and JavaScript.

### 5.2. Naming Conventions

Use unique prefixes (e.g., `myplugin_`) for functions, classes, and variables. Consider using namespaces for object-oriented code.

### 5.3. Security Practices

- **Sanitization:** Use functions like `sanitize_text_field()`, `sanitize_email()`, etc.
- **Validation:** Ensure data is in the expected format.
- **Escaping:** Use functions like `esc_html()`, `esc_url()`, `esc_attr()` when outputting data.
- **Nonces:** Protect forms and URLs to prevent CSRF.
  ```php
  $nonce = wp_create_nonce('my_nonce');
  if ( ! isset($_REQUEST['_wpnonce']) || ! wp_verify_nonce($_REQUEST['_wpnonce'], 'my_nonce') ) {
      wp_die('Invalid nonce!');
  }
  ```

### 5.4. Internationalization (i18n) & Localization (l10n)
- Wrap all user-facing strings in translation functions (`__()`, `_e()`, etc.).
- Load your text domain:
  ```php
  function mytheme_load_textdomain() {
      load_theme_textdomain('mytheme', get_template_directory() . '/languages');
  }
  add_action('after_setup_theme', 'mytheme_load_textdomain');
  ```

[To Top](#table-of-contents)

---

## 6. Debugging, Performance & Optimization

### 6.1. Debugging

Enable debugging in your `wp-config.php`:
```php
define('WP_DEBUG', true);
define('WP_DEBUG_LOG', true);
define('WP_DEBUG_DISPLAY', false);
```
Use tools such as [Query Monitor](https://wordpress.org/plugins/query-monitor/) for tracking errors and performance issues.

### 6.2. Performance Optimization

- **Caching:** Implement caching strategies (using Transients API or object caching).
- **Query Optimization:** Always use `$wpdb->prepare()` for secure database queries.
- **Asset Optimization:** Minify and combine CSS/JS files.

### 6.3. Profiling Tools

Consider using Xdebug and other profiling tools to identify performance bottlenecks.

[To Top](#table-of-contents)

---

### 7. Deployment & Maintenance

- **Version Control:** Use Git to manage your codebase and maintain a history of changes.
- **Staging Environment:** Always test your changes in a staging environment before deploying to production.
- **Backup Strategies:** Regularly back up your database and files.
- **Updates & Security:** Keep WordPress, themes, and plugins updated. Monitor for security patches and vulnerabilities.
- **Documentation & Comments:** Document your code thoroughly using DocBlocks (PHPDoc) and inline comments.

[To Top](#table-of-contents)

---

## 8. Tools & Resources

### 8.1. Official Documentation

- [WordPress Developer Handbook](https://developer.wordpress.org/)
- [WordPress Codex](https://codex.wordpress.org/)
- [Plugin Developer Handbook](https://developer.wordpress.org/plugins/)
- [Theme Developer Handbook](https://developer.wordpress.org/themes/)

### 8.2. WP-CLI

[WP-CLI Documentation](https://wp-cli.org/)

### 8.3. Additional Tools

- PHP CodeSniffer with WordPress Coding Standards.
- Debugging plugins like Query Monitor.

### 8.4. Community Resources

Forums, blogs, WordPress meetups, and Slack channels.

[To Top](#table-of-contents)