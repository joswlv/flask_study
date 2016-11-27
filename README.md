# flask_study
Make Restful API Server using Flask

# install flask

`sudo pip install Flask`

# install mysql-python

> export PATH=$PATH:/usr/local/mysql/bin/
>
> sudo pip install MySQL-python

`sudo pip install flask-mysql`


`sudo ln -s /usr/local/mysql/lib/libmysqlclient.|22.dylib /usr/lib/`

# setting nginx 

```bash
$ vi /etc/nginx/sites-available/default
server {
   listen 80; # 연결할 포트
   server_name 0.0.0.0;
   location / { try_files $uri @app; }
   location @app {
     include uwsgi_params;
     uwsgi_pass unix:socket파일이 위치할 경로;
     # ex) /home/server/uwsgi.sock
   }
}
```

# setting uWSGI

```bash
$ vi /etc/uwsgi/apps-available/uwsgi.ini
[uwsgi]
chdir = 프로젝트 경로
uid = 실행할계정
gid = 실행할계정
chmod-socket = 666
socket = socket파일이 위치할 경로
module = 모듈이름(실행할 파일 이름)
callable = 연결될 Flask 모듈이름
virtualenv = python 가상 환경 경로(virtualenv)
```




