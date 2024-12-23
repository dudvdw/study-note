### Commands

``` shell
systemctl enable v2ray
systemctl start v2ray
systemctl status v2ray
cd /usr/local/etc/v2ray
ls
nano config.json
cd
apt-get install nginx -y
apt-get install certbot python3-certbot-nginx
certbot --nginx
cd /etc/nginx/sites-available
ls
rm default
ls
nano default
cd
nginx -t
systemctl restart nginx
systemctl status nginx
systemctl restart v2ray
systemctl status v2ray
```

### V2Ray Server Side config.json (replace the UUID with yours)
path: /usr/local/etc/v2ray/config.json

```json
{
  "inbounds": [
    {
      "port": 10000,
      "listen":"127.0.0.1",
      "protocol": "vmess",
      "settings": {
        "clients": [
          {
            "id": "",
            "alterId": 0
          }
        ]
      },
      "streamSettings": {
        "network": "ws",
        "wsSettings": {
        "path": "/switch"
        }
      }
    }
  ],
  "outbounds": [
    {
      "protocol": "freedom",
      "settings": {}
    }
  ]
}
```

### cerbot Certificate

Use the following command to check the expiry date:
``` shell
certbot certificates
```

The Certbot packages on your system come with a cron job or systemd timer that will renew your certificates automatically before they expire. You will not need to run Certbot again, unless you change your configuration. You can test automatic renewal for your certificates bgit@github.com:dudvdw/study-note.gitgit@github.com:dudvdw/study-note.gitgit@github.com:dudvdw/study-note.gity running this command:
``` shell
sudo certbot renew --dry-run
```

### Nginx default file
path: /etc/nginx/sites-available/default
``` json
server {
  listen 80;
  server_name domain.com;
  return 301 https://domain.com$request_uri;
}

server {
  listen 443 ssl;
  listen [::]:443 ssl;
  server_name domain.com;

  ssl_certificate /etc/letsencrypt/live/domain.com/fullchain.pem;
  ssl_certificate_key /etc/letsencrypt/live/domain.com/privkey.pem;

  include /etc/letsencrypt/options-ssl-nginx.conf;
  ssl_dhparam /etc/letsencrypt/ssl-dhparams.pem;

  location / {
      proxy_pass https://domain2.com;   
      proxy_ssl_server_name on;
      proxy_redirect off;
      sub_filter_once off;
      sub_filter "domain2.com" $server_name;
      proxy_set_header Host "domain2.com";
      proxy_set_header Referer $http_referer;
      proxy_set_header X-Real-IP $remote_addr;
      proxy_set_header User-Agent $http_user_agent;
      proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
      proxy_set_header X-Forwarded-Proto https;
      proxy_set_header Accept-Encoding "";
      proxy_set_header Accept-Language "en";
  }

  location /switch {
    if ($http_upgrade != "websocket") {
        return 404;
    }
    proxy_redirect off;
    proxy_pass http://127.0.0.1:10000;
    proxy_set_header Upgrade $http_upgrade;
    proxy_set_header Connection "upgrade";
    proxy_set_header Host $host;

    # Show real IP in v2ray access.log
    proxy_set_header X-Real-IP $remote_addr;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
  }
}
```

### V2Ray Client Side Config

* The id should be same as the server config.

``` json
{
  "inbounds": [
    {
      "port": 1080,
      "listen": "127.0.0.1",
      "protocol": "socks",
      "sniffing": {
        "enabled": true,
        "destOverride": ["http", "tls"]
      },
      "settings": {
        "auth": "noauth",
        "udp": false
      }
    }
  ],
  "outbounds": [
    {
      "protocol": "vmess",
      "settings": {
        "vnext": [
          {
            "address": "domain.com",
            "port": 443,
            "users": [
              {
                "id": "",
                "alterId": 0
              }
            ]
          }
        ]
      },
      "streamSettings": {
        "network": "ws",
        "security": "tls",
        "wsSettings": {
          "path": "/switch"
        }
      }
    }
  ]
}
```

