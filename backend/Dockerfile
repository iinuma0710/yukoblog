FROM golang:1.20.4-alpine

WORKDIR /app

# # ホットリロードツール Air の導入
RUN apk update && apk add git
RUN go install github.com/cosmtrek/air@v1.43.0

# # Air でアプリケーションを起動
CMD ["air", "-c", ".air.toml"]