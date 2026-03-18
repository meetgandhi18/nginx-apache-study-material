# ⚖️ What is Load Balancing?

## 📌 Definition

Load Balancing means:

👉 Distributing incoming requests across multiple backend servers.

---

## 🧠 Basic Idea

### ❌ Without Load Balancing

User → Server1 (OVERLOADED)

---

### ✅ With Load Balancing

User → Load Balancer → Server1  
 → Server2  
 → Server3

👉 Traffic is distributed → system becomes fast and scalable.

---

## 🚀 Why We Need Load Balancing

- Handle high traffic
- Avoid server crashes
- Improve performance
- Ensure high availability

---

## ⚙️ NGINX Load Balancing

NGINX provides built-in load balancing using the **upstream block**.

### 🔁 Basic Config (Round Robin - Default)

```nginx
upstream backend {
    server 127.0.0.1:8001;
    server 127.0.0.1:8002;
    server 127.0.0.1:8003;
}

server {
    location / {
        proxy_pass http://backend;
    }
}
```

## 🔄 Request Flow Example

```bash
Req1 → Server1
Req2 → Server2
Req3 → Server3
Req4 → Server1
```

---

## 🔀 Load Balancing Methods in NGINX

### 1️⃣ Round Robin (Default)

Even distribution:

```bash
1 → S1
2 → S2
3 → S3
```

---

### 2️⃣ Least Connections

```nginx
upstream backend {
    least_conn;
    server 127.0.0.1:8001;
    server 127.0.0.1:8002;
}
```

## 👉 Sends request to the server with the least active connections.

---

### 3️⃣ IP Hash (Sticky Sessions)

```nginx
upstream backend {
    ip_hash;
    server 127.0.0.1:8001;
    server 127.0.0.1:8002;
}
```

## 👉 Same user → Same server

### Useful for:

```bash
login sessions
carts

```

---

### 4️⃣ Weight-Based Load Balancing

```nginx
upstream backend {
    server 127.0.0.1:8001 weight=3;
    server 127.0.0.1:8002 weight=1;
}
```

## 👉 Server1 gets more traffic than Server2.

## 🧩 Load Balancing in Apache

### 🔧 Enable Modules

```bash
a2enmod proxy
a2enmod proxy_balancer
a2enmod lbmethod_byrequests
```

### ⚙️ Basic Configuration

```nginx
<Proxy "balancer://mycluster">
    BalancerMember http://127.0.0.1:8001
    BalancerMember http://127.0.0.1:8002
</Proxy>

<VirtualHost *:80>
    ProxyPass "/" "balancer://mycluster/"
    ProxyPassReverse "/" "balancer://mycluster/"
</VirtualHost>
```

### 🔀 Load Balancing Methods in Apache

### 1️⃣ By Requests (Round Robin)

- Default method
- Equal distribution

---

### 2️⃣ By Traffic

- Based on data size

---

### 3️⃣ By Busyness

- Least busy server gets request

---

### 4️⃣ Sticky Sessions

```apache
<Proxy "balancer://mycluster">
    BalancerMember http://127.0.0.1:8001 route=1
    BalancerMember http://127.0.0.1:8002 route=2
</Proxy>
```
