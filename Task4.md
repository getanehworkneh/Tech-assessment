**Task 4: HTTPS Configuration**

To ensure your web service supports only **TLS 1.2** and disables older, insecure protocols (e.g., SSLv2, SSLv3, TLS 1.0, TLS 1.1), follow these steps:

**1\. Configure the Server (e.g., Nginx)**

**Steps**

1. **Edit Nginx Configuration**:
    - Locate the Nginx configuration file (usually /etc/nginx/nginx.conf or /etc/nginx/sites-available/default).
    - Modify the server block handling HTTPS traffic.
2. **Set SSL Protocols**:
    - Use the ssl_protocols directive to specify TLSv1.2 and disable older protocols.
3. **Set Strong Cipher Suites**:
    - Use the ssl_ciphers directive to enforce strong encryption algorithms.
4. **Reload Nginx**:
    - Apply the changes by reloading the Nginx configuration.

**2\. Example Nginx Configuration**

server {

listen 443 ssl;

server_name yourdomain.com;

\# SSL Certificate and Key

ssl_certificate /etc/ssl/certs/yourdomain.crt;

ssl_certificate_key /etc/ssl/private/yourdomain.key;

\# Enforce TLS 1.2 only

ssl_protocols TLSv1.2;

\# Strong cipher suites

ssl_ciphers 'ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES128-GCM-SHA256';

ssl_prefer_server_ciphers on;

\# Enable HSTS (Optional but recommended)

add_header Strict-Transport-Security "max-age=31536000; includeSubDomains" always;

\# Other configurations

location / {

root /var/www/html;

index index.html;

}

}

**3\. Reload Nginx**

After making changes, reload Nginx to apply the new configuration:

sudo nginx -t # Test configuration for syntax errors

sudo systemctl reload nginx # Reload Nginx

**4\. Verify Configuration**

Use tools like **SSL Labs** (<https://www.ssllabs.com/ssltest/>) or the openssl command to verify that only TLS 1.2 is supported:

openssl s_client -connect yourdomain.com:443 -tls1_2

**Key Points**

- **ssl_protocols TLSv1.2;**: Enforces TLS 1.2 only.
- **ssl_ciphers**: Specifies strong encryption algorithms.
- **HSTS**: Adds an HTTP header to enforce HTTPS for all future requests.

This setup ensures your web service is secure and compliant with modern encryption standards.
