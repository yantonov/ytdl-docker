FROM python:3.8-slim-buster

MAINTAINER Yury Antonov <yantonov@yandex.ru>

ENV APP_HOME=/root/ytdl

RUN \
    mkdir -p $APP_HOME

ADD files/requirements.txt /
RUN pip install -r /requirements.txt

WORKDIR $APP_HOME
