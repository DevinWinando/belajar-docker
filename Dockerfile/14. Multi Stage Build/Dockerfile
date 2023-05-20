FROM golang:alpine3.18 as builder

LABEL maintainer="Devin Winando"
LABEL email="devin.winando13@gmail.com"

COPY app/main.go /app/
RUN go build -o /app/main /app/main.go

FROM alpine:3

COPY --from=builder /app/main /app/

CMD /app/main
