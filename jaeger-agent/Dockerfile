FROM ppc64le/golang:1.13-alpine3.11
MAINTAINER Benoit Marolleau 
LABEL jaeger.version="1.18.1"

RUN apk add --update --no-cache ca-certificates
RUN apk --no-cache add curl

#FROM scratch
ARG TARGETARCH=ppc64le
#COPY --from=certs /etc/ssl/certs/ca-certificates.crt /etc/ssl/certs/ca-certificates.crt

RUN  curl -SL https://github.com/jaegertracing/jaeger/releases/download/v1.18.1/jaeger-1.18.1-linux-ppc64le.tar.gz \
    | tar -xzC /tmp \
    && rm -rf /tmp/jaeger-1.18.1-linux-ppc64le.tar.gz 
RUN  cp -r /tmp/jaeger-1.18.1-linux-ppc64le/* /go/bin

#COPY jaeger-1.18.1-linux-ppc64le/jaeger-agent  /go/bin
EXPOSE 5775/udp 6831/udp 6832/udp 5778
ENTRYPOINT ["/go/bin/jaeger-agent"]
