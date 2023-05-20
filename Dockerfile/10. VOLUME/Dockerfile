FROM golang:alpine3.18

LABEL maintainer="Devin Winando"
LABEL email="devin.winando13@gmail.com"

ENV APP_PORT=8080
ENV APP_DATA=/logs

RUN mkdir ${APP_DATA}
RUN mkdir app
COPY file/main.go app

EXPOSE ${APP_PORT}
VOLUME ${APP_DATA}

CMD go run app/main.go
