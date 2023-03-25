FROM python:3.8-slim-buster

MAINTAINER Yury Antonov <yantonov@yandex.ru>

ENV APP_HOME=/root/ytdl

RUN \
    mkdir -p $APP_HOME

ADD files/requirements.txt /
RUN pip install -r /requirements.txt

RUN apt-get update && apt-get install -y git
RUN pip install git+https://github.com/ytdl-org/youtube-dl.git

WORKDIR $APP_HOME
