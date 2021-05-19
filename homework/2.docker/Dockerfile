FROM golang:1.14

ARG VERSION
LABEL Author="Vitaly vitaly@geekbrains.ru"\
      Version=${VERSION}

ENV PORT=8080

COPY golang /usr/src/app
RUN cd /usr/src/app && \
    go build -o /usr/local/bin/goapp && \
    chmod +x /usr/local/bin/goapp

EXPOSE 8080

USER 65534:65534
ENTRYPOINT [ "/usr/local/bin/goapp" ]