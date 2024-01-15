FROM mcr.microsoft.com/dotnet/sdk:8.0.101-alpine3.19-amd64 AS build

ADD zint-2.13.0-src.tar.gz /tmp/
WORKDIR /tmp/zint-2.13.0-src

RUN apk add --no-cache build-base cmake \
    && cmake . \
    && make \
    && make install

FROM mcr.microsoft.com/dotnet/aspnet:8.0.1-alpine3.19-amd64 AS final
COPY --from=build /usr/local/lib/libzint.so.2.13.0.0 /usr/local/lib/libzint.so.2.13.0.0
COPY --from=build /usr/local/lib/libzint.so.2.13 /usr/local/lib/libzint.so.2.13
COPY --from=build /usr/local/lib/libzint.so /usr/local/lib/libzint.so
COPY --from=build /usr/local/bin/zint /usr/local/bin/zint

COPY ["chromium-120.0.6099.216-r0.apk", "/tmp/chromium-120.0.6099.216-r0.apk"]
WORKDIR /tmp
RUN apk add --no-cache ./chromium-120.0.6099.216-r0.apk

WORKDIR /
RUN rm -rf /tmp
CMD ["sh"]