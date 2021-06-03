FROM golang:1.14 as build

ENV CGO_ENABLED=0 \
    GOOS=linux \
    GOARCH=amd64 \
    LD_FLAGS="-w -s"

COPY golang /usr/src/app
RUN cd /usr/src/app && \
    go build -ldflags="$LD_FLAGS" -o /tmp/build/goapp

FROM scratch
ARG VERSION
LABEL Author="Vitaly vitaly@geekbrains.ru"\
      Version=${VERSION}

ENV PORT=8080

COPY --from=build /tmp/build/goapp /usr/bin/

EXPOSE 8080

USER 65534:65534
ENTRYPOINT [ "goapp" ]
