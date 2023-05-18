FROM golang:alpine3.16 as build
WORKDIR /app
COPY go.mod ./
COPY go.sum ./
RUN go mod download
COPY *.go ./
RUN go build -o /keren

FROM alpine:latest
WORKDIR /
COPY --from=build /keren /keren
EXPOSE 8000
ENTRYPOINT ["/keren"]