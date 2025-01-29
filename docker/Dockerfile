FROM python:3.9-slim-buster

MAINTAINER Yury Antonov <1390348+yantonov@users.noreply.github.com>

ENV APP_HOME=/root/ytdl

RUN \
    mkdir -p $APP_HOME

ADD files/requirements.txt /
RUN pip install -r /requirements.txt

RUN apt update && apt install -y git curl p7zip
RUN \
    mkdir -p /opt && \
    cd /opt/ && \
    curl -L 'https://github.com/BtbN/FFmpeg-Builds/releases/download/latest/ffmpeg-master-latest-linux64-gpl.tar.xz' --output ffmpeg.tar.xz && \
    7zr x ffmpeg.tar.xz && \
    tar xf ffmpeg.tar && \
    mv ffmpeg-master-latest-linux64-gpl ffmpeg

ENV PATH=/opt/ffmpeg/bin:$PATH

# RUN pip install git+https://github.com/ytdl-org/youtube-dl.git

WORKDIR $APP_HOME
