# react-django-restframework

# This repository is demo that reactjs + django

# create docker-compose.yml file
```
version: "3.9"

services:
  reactjs:
    container_name: reactjs
    build: ./reactjs
    ports:
      - 3000:3000
    volumes:
      - ./reactjs/my-app:/app
    command:
      sh -c "npm install && npm start"

  django:
    container_name: django
    build: ./django
    ports:
      - 8000:8000
    volumes:
      - ./django/app:/app
    command:
      sh -c "python3 manage.py runserver 0.0.0.0:8000"
```

# create reactjs and django folder
```
mkdir -p reactjs
mkdir -p django
mkdir -p django/app
```

# create 2 Dockerfile in each directorys
reactjs/Dockerfile
```
FROM node:17-alpine
WORKDIR /app
```
django/Dockerfile
```
# see https://www.geeksforgeeks.org/python-django-test-driven-development-of-web-api-using-drf-docker/
FROM python:3.8-alpine
ENV PYTHONBUFFERED=1

COPY ./requirements.txt /requirements.txt
RUN pip3 install -r requirements.txt

RUN mkdir /app
WORKDIR /app
COPY ./app /app
RUN adduser -D user
USER user
```

# create requirements.txt in django directory
```
Django==3.2.12
djangorestframework==3.13.1
```

# run docker-compose command
```
docker-compose run reactjs sh -c "npx create-react-app ."
```
```
docker-compose run django sh -c "django-admin startproject myapp ." 
```
```
docker-compose run django sh -c "python manage.py startapp api"
```
```
docker-compose build
```
```
docker-compose up -d
```
