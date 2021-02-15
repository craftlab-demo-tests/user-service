FROM golang:1.15 AS build
WORKDIR /go/src/github.com/craftlab-demo-tests/user-service/
COPY go ./go
COPY main.go .

ENV CGO_ENABLED=0
RUN go get -d -v ./...

RUN go test ./...
RUN go build -a -installsuffix cgo -o openapi .

FROM scratch AS runtime
COPY --from=build /go/src/github.com/craftlab-demo-tests/user-service/openapi ./
EXPOSE 8080/tcp
ENTRYPOINT ["./openapi"]
