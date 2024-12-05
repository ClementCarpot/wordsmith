FROM golang:1.21-alpine AS golang-alpine

WORKDIR /app

COPY dispatcher.go ./
COPY static ./static

RUN go build dispatcher.go

FROM scratch

WORKDIR /app

COPY --from=golang-alpine /app/dispatcher ./
COPY --from=golang-alpine /app/static ./static

EXPOSE 8080

ENTRYPOINT ["./dispatcher"]
