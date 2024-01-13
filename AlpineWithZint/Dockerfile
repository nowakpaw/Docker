FROM alpine:latest

RUN apk update && \
    apk upgrade && \
    apk add --no-cache bash

# ADD is also unpacking files from archive:
ADD zint-2.13.0-src.tar.gz /zint-src

WORKDIR /zint-src/zint-2.13.0-src
RUN apk add build-base cmake \
    && cmake . \
    && make \
    && make install

WORKDIR /
RUN apk del build-base cmake \
    && rm -rf /zint-src
CMD ["sh"]