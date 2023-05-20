FROM golang:alpine3.18

LABEL maintainer="Devin Winando"
LABEL email="devin.winando13@gmail.com"

ENV APP_PORT=8080

WORKDIR /app
COPY file/main.go app

EXPOSE ${APP_PORT}

CMD go run main.go
