# auth-api/Dockerfile
FROM golang:1.21 AS build-stage
WORKDIR /app
COPY go.mod go.sum ./
RUN go mod download
COPY . .
RUN CGO_ENABLED=0 GOOS=linux go build -o auth-api .

FROM alpine:latest
WORKDIR /root/
COPY --from=build-stage /app/auth-api .
CMD ["./auth-api"]
EXPOSE 8081