# 🌐 Apache Web Server

## 📌 Definition

Apache HTTP Server (commonly called Apache) is an open-source web server that delivers web pages and APIs to users over the internet.

- Created in 1995
- Maintained by the Apache Software Foundation
- Once the most popular web server in the world

---

## 🚀 Why Apache Was So Popular

Apache became widely adopted because it is:

- Free and open source
- Highly flexible
- Easy to configure
- Works seamlessly with PHP

### 🧱 LAMP Stack

Apache is part of the LAMP stack:

LAMP Stack:

- Linux
- Apache
- MySQL
- PHP

Used in:

- WordPress (early days)
- Blogs
- Forums
- Traditional web apps

---

## ⚙️ What Apache Actually Does

Apache handles HTTP requests from browsers.

### 📥 Example Request

GET /products HTTP/1.1  
Host: example.com

### 🔍 What Apache Does

- Checks if it's a static file
- Checks if it's a script (PHP)
- Checks application routes

Then returns the correct response.

---

## 🔄 Request Flow

Browser  
↓  
Apache Web Server  
↓  
Application (PHP / Laravel)  
↓  
Database  
↓  
Response → Browser

---

## 🧠 Apache Architecture

Apache uses a process/thread-based model.

User1 → Thread1  
User2 → Thread2  
User3 → Thread3

### ⚠️ Key Point

- More users = More threads
- More threads = More memory usage

This is why NGINX became popular.

---

## 🧩 Apache Modules (Very Important)

Apache is modular (features added via modules).

| Module       | Purpose           |
| ------------ | ----------------- |
| mod_php      | Run PHP code      |
| mod_rewrite  | URL rewriting     |
| mod_ssl      | HTTPS support     |
| mod_headers  | Control headers   |
| mod_security | Security firewall |

### 🔧 Enable Module

```bash
a2enmod rewrite
sudo systemctl restart apache2
```

## 📁 Apache Configuration Files

Apache configuration usually lives in:

/etc/apache2

### Important Files

- apache2.conf
- ports.conf
- sites-available/
- sites-enabled/

### 🧾 Example Configuration

```apache
<VirtualHost *:80>
    ServerName example.com
    DocumentRoot /var/www/html
</VirtualHost>
```

## 📄 The Famous .htaccess File

One of Apache's most powerful features is:

.htaccess

It allows directory-level configuration.

### 📍 Example Location

/var/www/html/.htaccess

### 🔧 You Can Configure

- Redirects
- Authentication
- Caching
- URL rewriting

### 🧾 Example

```apache
RewriteEngine On
RewriteRule ^user/(.*)$ profile.php?id=$1
```

This feature is one reason shared hosting providers love Apache.

---

## 🌍 Apache Virtual Hosts

Apache can host multiple websites on one server.

### 🧾 Examples

- example.com
- api.example.com
- blog.example.com

### ⚙️ Configuration

```apache
<VirtualHost *:80>
    ServerName example.com
</VirtualHost>

<VirtualHost *:80>
    ServerName blog.example.com
</VirtualHost>
```

This is called Virtual Hosting.

---

## ✅ Advantages of Apache

- Very flexible
- Huge ecosystem
- Supports .htaccess
- Easy PHP integration
- Works well for shared hosting

---

## ❌ Disadvantages of Apache

- Higher memory usage
- Slower with many users
- Thread-based architecture

This is why modern high-traffic sites often prefer NGINX.

---

## 🎯 Interview Question

### ❓ Why is Apache still used even though NGINX is faster?

- .htaccess support
- Huge module ecosystem
- Backward compatibility
- Shared hosting environments

```

```
