# django start project in docker
해당 레파지토리는 docker-compose로 django/postgres 를 쉽게 시작하기 위해 만들게 됐다. 

## Set Up
### 1. Dockerfile 이용해서 이미지 빌드
```shell
$ docker build .
```
이미지에 이름과 태그를 설정해주고 싶다면 아래와 같이 하면 된다.
```shell
$ docker build -t [image name]:[tag] .
```

### 2. django 프로젝트 생성
```shell
$ docker-compose run web django-admin startproject [project_name] .
```

### 3. database 연결
```python
# settings.py
import os

# Database
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': os.environ.get('POSTGRES_NAME'),
        'USER': os.environ.get('POSTGRES_USER'),
        'PASSWORD': os.environ.get('POSTGRES_PASSWORD'),
        'HOST': 'db',
        'PORT': 5432,
    }
}
```

### 4. 컨테이너 구동
```shell
$ docker compose up
```



