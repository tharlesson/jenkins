FROM golang:1.26-alpine AS builder
WORKDIR /src
COPY . .
RUN CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build -o /out/app ./cmd/app

FROM alpine:3.23
RUN adduser -D -u 10001 appuser
USER appuser
COPY --from=builder /out/app /app
ENTRYPOINT ["/app"]
