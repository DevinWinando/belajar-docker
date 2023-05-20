FROM golang:alpine3.18

LABEL maintainer="Devin Winando"
LABEL email="devin.winando13@gmail.com"

RUN mkdir app
COPY file/main.go app

EXPOSE 8080

CMD go run app/main.go
