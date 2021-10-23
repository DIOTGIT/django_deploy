## Set Up Django with Postgres, Nginx, and Gunicorn on Ubuntu 20.04
infó: https://arctype.com/blog/install-django-ubuntu/, https://gist.github.com/epicserve/1332256/cfa20cc864b2c462a8d4c6bdf485c3157a9fa0af

**set up a basic project**
 - mkdir ~/Dj_live
 - cd ~/Dj_live
 - python3 -m venv .venv
 - . ./.venv/bin/activate
 - pip install django gunicorn psycopg2-binary
 - django-admin.py startproject Dj_project .
 - nano Dj_project/settings.py
---
```

    ALLOWED_HOSTS = ['django.example.com', 'localhost']
    
    STATIC_URL = '/static/'
    import os
    STATIC_ROOT = os.path.join(BASE_DIR, 'static/')
```
---
- ./manage.py makemigrations
- ./manage.py migrate
- ./manage.py createsuperuser (Dj/Dj)
- ./manage.py collectstatic
- ./manage.py runserver 0.0.0.0:8000
---
- gunicorn --bind 0.0.0.0:8000 Dj_project.wsgi
- CTRL+C
- deactivate
---
- sudo nano /etc/systemd/system/gunicorn.socket
```
[Unit]
Description=gunicorn socket
[Socket]
ListenStream=/run/gunicorn.sock
[Install]
WantedBy=sockets.target
```
---
- nano /etc/systemd/system/gunicorn.service
```
[Unit]
Description=gunicorn daemon
Requires=gunicorn.socket
After=network.target

[Service]
User=ubi
Group=www-data
WorkingDirectory=/home/ubi/PY/Dj_live 
ExecStart=/home/ubi/PY/Dj_live/.venv/bin/gunicorn \
          --access-logfile - \
          --workers 3 \
          --bind unix:/run/gunicorn.sock \
          Dj_live.wsgi:application

[Install]
WantedBy=multi-user.target

```
---

- sudo chown -R www-data:root ~/PY/Dj_live
- systemctl daemon-reload
- systemctl start gunicorn.socket
- systemctl enable gunicorn.socket
---
- sudo apt-get install python3-pip python3-dev libpq-dev curl nginx -y
- systemctl start nginx
- systemctl enable nginx
- sudo nano /etc/nginx/sites-available/Dj_live
```
    server {
        listen 80;
        server_name 192.168.1.180;
    
        location = /favicon.ico { access_log off; log_not_found off; }
        location /static/ {
            root /home/ubi/PY/Dj_live;
        }
    
        location / {
            include proxy_params;
            proxy_pass http://unix:/run/gunicorn.sock;
        }
    }
```
- sudo ln -s /etc/nginx/sites-available/Dj_live /etc/nginx/sites-enabled
- sudo nginx -t
- sudo systemctl restart nginx
- sudo ufw delete allow 8000
- sudo ufw allow 'Nginx Full'
