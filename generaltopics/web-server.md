# 🌐 Web Server Fundamentals

## 📌 What is a Web Server?

A **Web Server** is software that:

1. Receives a request from a client (browser or app)
2. Processes the request
3. Sends a response back to the client

### 📦 The Response Can Be:

- HTML page
- JSON API response
- Image
- Video
- File download

---

## 🔍 Example

When you type:

https://google.com

Your browser sends a request like:

GET / HTTP/1.1  
Host: google.com

The web server responds:

HTTP/1.1 200 OK  
Content-Type: text/html

👉 Then the HTML page loads in your browser.

---

# 🔄 Basic Request Flow

Browser → Internet → Web Server → Response → Browser

### 📌 Step-by-Step Flow

User types URL  
↓  
Browser sends HTTP request  
↓  
Web Server processes request  
↓  
Server sends response  
↓  
Browser renders page

---

# 🧩 Types of Servers in Web Architecture

| Server Type        | Example           |
| ------------------ | ----------------- |
| Web Server         | Apache, NGINX     |
| Application Server | Node.js, PHP-FPM  |
| Database Server    | MySQL, PostgreSQL |
| Proxy Server       | NGINX, HAProxy    |

---

# ⚙️ Responsibilities of a Web Server

A web server handles multiple important tasks:

---

## 1️⃣ HTTP Requests

Example:

GET /products  
POST /login

---

## 2️⃣ Static Files

Static files are files that **do not change**.

### 📁 Examples

- HTML
- CSS
- JavaScript
- Images
- Videos

### 📥 Example Request

GET /logo.png

👉 Server simply returns the file.

---

## 3️⃣ Routing Requests

Examples:

/products → Products Controller  
/login → Login Handler

---

## 4️⃣ Security

Web servers manage:

- SSL Certificates
- Authentication
- IP Blocking
- Rate Limiting

---

# 📊 Load Management

Servers must handle multiple users at the same time.

Example:

1 user  
10 users  
100 users  
1000 users  
100000 users

👉 Handling large traffic efficiently is where **NGINX vs Apache architecture** becomes important.

---

# ⚡ Static vs Dynamic Response

## 🟢 Static Response

Server directly returns a file.

Example:

GET /image.png

Response:

image.png

✅ Very fast (no processing required)

---

## 🔵 Dynamic Response

Server executes backend code.

Example:

GET /profile?id=15

### 🔄 Processing Flow

Request → PHP → Database → Response

---

# 🎯 Why Web Servers Are Needed

Without a web server:

- Browsers cannot access backend code
- Requests cannot be handled
- Files cannot be served
- APIs cannot respond

👉 A **Web Server acts as a gateway between the Internet and your application.**
