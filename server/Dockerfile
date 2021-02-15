FROM golang:alpine AS build
WORKDIR /go/src/github.com/craftlab-demo-tests/user-service/
COPY go ./go
COPY main.go .

ENV CGO_ENABLED=0
RUN go get -d -v ./...

RUN go tests ./...
RUN go build -a -installsuffix cgo -o openapi .

FROM scratch AS runtime
COPY --from=build /go/src/github.com/craftlab-demo-tests/user-service/openapi ./
EXPOSE 8080/tcp
ENTRYPOINT ["./openapi"]
