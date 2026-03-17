# What is Reverse Proxy

    Client → Reverse Proxy → Backend → Response → Client

    Client talks only to proxy
    Backend is hidden

## Nginx as Reverse Proxy

### How Nginx Does it

    Nginx is built for reverse proxying(this is the strongest feature)

### Basic config

    server{
        listen 80;

        location /{
            proxy_pass http://127.0.0.1:8000;
        }
    }

    What Happens

        User → NGINX → Backend (port 8000) → Response → User

    Adavnce e.x:-

    server{
        listen 80;

        location /api {
        proxy_pass http://node-app:3000;
        }

        location /php {
        proxy_pass http://laravel-app:9000;
        }
    }

    NGINX routes requests based on URL

### Why Nginx is best for reverse Proxy

    ✔ Event-driven (fast)
    ✔ Low memory usage
    ✔ Built-in proxy features
    ✔ Handles thousands of requests

## Apache as Reverse Proxy

    Apache uses modules for reverse proxy.

### Enable it

    sudo a2enmod proxy
    sudo a2enmod proxy_http

### Basic Config

    <VirtualHost *:80>
        ProxyPass "/" "http://127.0.0.1:8000/"
        ProxyPassReverse "/" "http://127.0.0.1:8000/"
    </VirtualHost>

    What happens:-
        User → Apache → Backend → Response → User

### Difference from Nginx

    Apache:
        Uses modules
        Slightly heavier
        Not as fast under high load

### Reverse Proxy is not just routing - it can also:

    cache response
    compress data
    handle ssl
    block attacks

    E.x:-
        HTTPS → NGINX → HTTP → Backend

### 1.How To handle SSL Using Revserse Proxy

    Concept:-
        Instead of backend handling HTTPS:
            Client -> backend (HTTPS)
        We do:
            Client -> Reverse Proxy (HTTPS) -> Backend(HTTP)

        Reverse Proxy handels the SSL
        Backend Stays simple

### Nginx

    config:
        server {
            listen 443 ssl;
            server_name example.com;

            ssl_certificate /etc/ssl/cert.pem;
            ssl_certificate_key /etc/ssl/key.pem;

            location / {
                proxy_pass http://127.0.0.1:8000;
            }
        }

### Apache

    Enable SSL:
        a2enmod ssl

    Config:
        <VirtualHost \*:443>
            SSLEngine on
            SSLCertificateFile /etc/ssl/cert.pem
            SSLCertificateKeyFile /etc/ssl/key.pem

            ProxyPass "/" "http://127.0.0.1:8000/"
            ProxyPassReverse "/" "http://127.0.0.1:8000/"
        </VirtualHost>

### 2.Caching (Super Important for Performance)

    Concept:-
        Instead of hitting backend every time:-
            User → Proxy → Backend → Response

    We do:-
        User → Proxy → Cached Response (FAST ⚡)

### Nginx

    proxy_cache_path /tmp/nginx_cache levels=1:2 keys_zone=my_cache:10m;

    server {
        location / {
            proxy_cache my_cache;
            proxy_pass http://127.0.0.1:8000;
            proxy_cache_valid 200 10m;
        }
    }

    Now responses are cached for 10 minutes

### Apache

    Enable modules:
        a2enmod cache
        a2enmod cache_disk

    config:
        CacheEnable disk /
        CacheRoot "/var/Cache/apache2/mode_cache_disk"

### 3.Compression (Reduce Response Size)

    Concept:-
        Without compression:
            Response = 100KB
        With compression:
            Response = 20KB

    Faster Loading 🚀

### Nginx

    gzip on;
    gzip_types text/plain text/css application/json application/javascript;

### Apche

    Enable:
        a2enmod deflate
    Config:
        AddOutputFilterByType DEFLATE text/html text/css application/javascript

### 4.Security (Basic Protection)

    What Revserse Proxy Can Do
        Hide backend Server
        Block malicious IPs
        Limit requests(rate limiting)
        Add headres

### Nginx

    Block IP:
        deny 192.168.1.10;

    Rate Limiting:
        limit_req_zone $binary_remote_addr zone=api_limit:10m rate=5r/s;

        location /api {
            limit_req zone=api_limit;
        }

### Apache

    Block IP:
        <RequireAll>
            Require all granted
            Require not ip 192.168.1.10
        </RequireAll>

    Rate Limiting (basic):
        <IfModule mod_ratelimit.c>
            SetOutputFilter RATE_LIMIT
            SetEnv rate-limit 400
        </IfModule>
