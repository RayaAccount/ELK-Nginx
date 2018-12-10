# ELK-Nginx
for Nginx HTTP Caching and Compression
Open up your /etc/nginxnginx.conf file
Uncomment the following chunk:
        gzip on;
        gzip_disable "MSIE [1-6]\.(?!.*SV1)";

        gzip_vary on;
        gzip_proxied any;
        gzip_comp_level 6;
        gzip_buffers 16 8k;
        gzip_http_version 1.1;
        gzip_types text/plain text/css application/json application/x-javascript text/xml application/xml application/xml+rss text/javascript;
Save the file and restart nginx.

To enable HTTP Caching, head out into /etc/nginx/sites-enabled/<your-site-config-file> and make the following changes:
  #enable caching         location ~* \.html$ {
                expires -1;
        }

        location ~* \.(css|js|gif|jpe?g|png)$ {
                expires 15d;
                add_header Pragma public;
                add_header Cache-Control "public, must-revalidate, proxy-revalidate";
        }
        
Another restart of nginx and you must notice a decent improvement in performance.

A quick way to check if your settings are in place is by using curl.

  $ curl -I cruisemaniac.com/favicon.png
      HTTP/1.1 200 OK Server: nginx/1.1.19 Date: Sat, 07 Dec 2013 05:26:48 GMT Content-Type: image/png Content-Length: 34402 Last-Modified: Fri, 06 Dec 2013 23:57:03 GMT Connection: keep-alive Expires: Sun, 22 Dec 2013 05:26:48 GMT Cache-Control: max-age=1296000 Pragma: public Cache-Control: public, must-revalidate, proxy-revalidate Accept-Ranges: bytes


        
