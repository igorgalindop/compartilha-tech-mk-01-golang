FROM golang:latest as development

RUN apt-get update && apt-get install -y inotify-tools
RUN go install github.com/githubnemo/CompileDaemon@latest

WORKDIR /app

COPY go.mod go.sum ./

RUN ls -la && \
    go mod download

COPY . .

CMD CompileDaemon -build="go build -o bin/main ./cmd/api/main.go" -command="./bin/main" -exclude-dir=".git"