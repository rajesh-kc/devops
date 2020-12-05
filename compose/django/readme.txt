# 1
Add the following content to the Dockerfile.

FROM python:3
ENV PYTHONUNBUFFERED=1
WORKDIR /code
COPY requirements.txt /code/
RUN pip install -r requirements.txt
COPY . /code/


# 2
requirements.txt


Django>=3.0,<4.0
psycopg2-binary>=2.8



# 3
docker-compose.yml

version: "3.8"
   
services:
  db:
    image: postgres
    environment:
      - POSTGRES_DB=postgres
      - POSTGRES_USER=postgres
      - POSTGRES_PASSWORD=postgres
  web:
    build: .
    command: python manage.py runserver 0.0.0.0:8000
    volumes:
      - .:/code
    ports:
      - "8000:8000"
    depends_on:
      - db



# 5
RUN

$ sudo docker-compose run web django-admin startproject composeexample .
$ sudo chown -R $USER:$USER .


# 6
edit the composeexample/settings.py file

# settings.py
   
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'postgres',
        'USER': 'postgres',
        'PASSWORD': 'postgres',
        'HOST': 'db',
        'PORT': 5432,
    }
}

# 7
RUN

$ docker-compose up -d


# Ref:
https://docs.docker.com/compose/django/
