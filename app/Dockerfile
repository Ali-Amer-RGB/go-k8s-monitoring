FROM golang:1.22-alpine AS build
WORKDIR /src
COPY go.mod .
RUN go mod download
COPY . .
RUN CGO_ENABLED=0 GOOS=linux go build -o app main.go

FROM alpine:3.20
WORKDIR /app
COPY --from=build /src/app .
EXPOSE 8080
ENV PORT=8080
CMD ["./app"]
