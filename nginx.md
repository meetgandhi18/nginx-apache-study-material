# 🚀 What is NGINX?

NGINX is a high-performance web server used to:

- Serve websites
- Act as a reverse proxy
- Load balance servers
- Cache content
- Handle high traffic

It was created in 2004 by Igor Sysoev.

---

## ❓ Why NGINX Was Created

As the internet grew, web servers like Apache faced a major issue called the **C10K Problem**.

---

## ⚠️ What is the C10K Problem?

It refers to handling **10,000 concurrent connections efficiently**.

Older servers used a thread/process per connection:

Example:

User1 → Thread1  
User2 → Thread2  
User3 → Thread3

If 10,000 users connect:

10,000 users → 10,000 threads

### 🚨 Problems

- Huge memory usage
- CPU overload
- Server crashes

👉 NGINX was built specifically to solve this problem.

---

## 🧠 Core Idea Behind NGINX

NGINX uses an **event-driven architecture**.

Instead of creating a thread per user, it uses a few worker processes to handle many connections asynchronously.

Example:

Worker Process

- User1
- User2
- User3
- User4
- User1000

### 🔑 Key Idea

Few workers → Many users

### ✅ Benefits

- Extremely fast
- Memory efficient
- Ideal for high-traffic systems

---

## 🔧 What NGINX is Used For

NGINX is more than just a web server.

| Role          | Description                 |
| ------------- | --------------------------- |
| Web Server    | Serve static files          |
| Reverse Proxy | Forward requests to backend |
| Load Balancer | Distribute traffic          |
| Cache Server  | Cache responses             |
| API Gateway   | Manage microservices        |

---

## 🔄 Example Request Flow

API Request:

GET /api/products

Flow:

Browser  
↓  
NGINX  
↓  
Backend (Laravel / Node / Python)  
↓  
Database  
↓  
Response → Browser

---

## 📂 Static File Handling in NGINX

NGINX is extremely fast at serving static files.

Example:

GET /logo.png

Flow:

Client → NGINX → File → Response

👉 No backend required.

---

## ⚙️ Dynamic Requests in NGINX

NGINX does **not execute PHP directly**.

It forwards requests to **PHP-FPM**.

Flow:

Browser  
↓  
NGINX  
↓  
PHP-FPM  
↓  
Laravel  
↓  
Database

### 🧾 Example Config

```nginx
location ~ \.php$ {
    fastcgi_pass unix:/run/php/php8.2-fpm.sock;
}
```

## 🏗️ Basic NGINX Architecture

NGINX has three main components:

### 1️⃣ Master Process

**Responsibilities:**

- Read configuration
- Manage worker processes
- Restart workers

---

### 2️⃣ Worker Processes

Workers handle:

- Client requests
- Network connections
- File serving

**Example:**

Master  
├── Worker1  
├── Worker2  
├── Worker3

👉 Each worker can handle thousands of connections.

---

### 3️⃣ Event Loop

Workers use an event loop.

Instead of blocking operations, they process events like:

- New request
- File ready
- Socket response
- Connection closed

👉 This makes NGINX non-blocking.

---

## ⚙️ Example of NGINX Configuration

Main config file:

/etc/nginx/nginx.conf

### 🧾 Example Server Config

```nginx
server {
    listen 80;
    server_name example.com;

    location / {
        root /var/www/html;
        index index.html index.php;
    }
}
```

### 📌 Meaning

- Listen on port 80
- Serve website example.com
- Files served from /var/www/html

---

## ⚡ NGINX Performance Advantages

NGINX is famous for:

| Feature                   | Benefit               |
| ------------------------- | --------------------- |
| Event-driven architecture | Handles many users    |
| Low memory usage          | Efficient             |
| High concurrency          | Thousands of requests |
| Fast static serving       | Ideal for CDNs        |

---

## 🚀 Capabilities

- High scalability
- Reverse proxy
- Load balancing
- Caching
- Microservices support

```

```
