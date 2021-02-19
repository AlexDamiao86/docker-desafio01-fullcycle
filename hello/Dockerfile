FROM golang:1.14-alpine AS build

WORKDIR /src/
COPY hello.go go.* /src/
RUN CGO_ENABLED=0 go build -a -ldflags '-extldflags "-static" -s -w' -o /bin/hello

FROM scratch
COPY --from=build /bin/hello /bin/hello
ENTRYPOINT ["/bin/hello"]