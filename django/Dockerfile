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
