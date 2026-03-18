# 🚀 NGINX & Apache Study Material

A complete learning repository covering **Web Server Fundamentals, Apache, NGINX, Reverse Proxy, and Load Balancing**.

---

## 📚 About This Repo

This repository is designed for:

- 📖 Beginners learning backend infrastructure
- 🧑‍💻 Developers preparing for interviews
- ⚙️ Engineers working with real-world server setups

---

## 📁 Folder Structure

```
nginx-apache-study-material/
│
├── general-topics/
│   ├── web-server.md
│   ├── reverse-proxy.md
│   └── load-balancer.md
│
├── apache/
│   ├── apache.md
│   ├── apache-commands.txt
│   ├── apache.txt
│   └── apache-mpm.md
│
├── nginx/
│   ├── nginx.md
│   └── nginx-commands.txt
```

---

## 🌐 General Topics

### 📘 Web Server Fundamentals

- What is a web server
- Request → Response lifecycle
- Static vs Dynamic content
- Types of servers (Web, App, DB)

### 🔁 Reverse Proxy

- Client → Proxy → Backend flow
- SSL termination
- Caching & compression
- Security & request routing

### ⚖️ Load Balancing

- Traffic distribution across servers
- Scaling applications

**Methods:**

- Round Robin
- Least Connections
- IP Hash (Sticky Sessions)
- Weighted

---

## 🧱 Apache

### 📘 Concepts

- Process/thread-based architecture
- Modules (`mod_php`, `mod_rewrite`, etc.)
- Virtual Hosts
- `.htaccess` usage

### ⚙️ Commands

- Start / Stop / Restart Apache
- Enable sites & modules
- Config testing & debugging

### 🧠 Advanced (MPM)

- Prefork
- Worker
- Event

---

## ⚡ NGINX

### 📘 Concepts

- Event-driven architecture
- Solves C10K problem
- Reverse proxy & load balancing
- Static file optimization

### ⚙️ Commands

- Start / Stop / Reload NGINX
- Config testing (`nginx -t`)
- Logs & debugging

---

## 🔗 Key Concepts

### 🌐 Web Server

Handles HTTP requests and responses.

### 🔁 Reverse Proxy

Acts as an intermediary between client and backend.

### ⚖️ Load Balancer

Distributes traffic across multiple servers.

---

## 🧠 Apache vs NGINX

| Feature      | Apache 🧱      | NGINX ⚡      |
| ------------ | -------------- | ------------- |
| Architecture | Thread/Process | Event-driven  |
| Performance  | Moderate       | High          |
| Memory Usage | Higher         | Lower         |
| PHP Handling | Built-in       | PHP-FPM       |
| .htaccess    | Supported      | Not supported |

---

## 🧪 Common Workflows

### Apache

```
sudo apachectl configtest
sudo systemctl reload apache2
tail -f /var/log/apache2/error.log
```

### NGINX

```
sudo nginx -t
sudo systemctl reload nginx
tail -f /var/log/nginx/error.log
```

---

## 🚀 Real-World Architecture

```
User
 ↓
NGINX (Reverse Proxy + Load Balancer)
 ↓
Multiple Backend Servers
 ↓
Database
```

---

## 🎯 Goal of This Repository

- Build strong backend fundamentals
- Understand real-world server architecture
- Prepare for system design & interviews
- Learn Apache & NGINX practically

---

## 👨‍💻 Author

**Meet Gandhi**

---

## ⭐ Support

If you found this helpful, consider giving it a ⭐ on GitHub!
