FROM python:3.8.2-slim-buster

ENV DEVPI_CLIENT_VERSION 5.1.1
ENV DEVPI_SERVER_VERSION 5.4.0

RUN addgroup --system --gid 1000 devpi \
 && adduser --disabled-password --system --uid 1000 \
      --home /data --shell /sbin/nologin --gid 1000 devpi

RUN pip install --no-cache-dir -q "devpi-client==$DEVPI_CLIENT_VERSION" \
 && pip install --no-cache-dir -q "devpi-server==$DEVPI_SERVER_VERSION"

VOLUME /data

COPY entrypoint /entrypoint
RUN chmod +x /entrypoint

USER devpi
ENV HOME /data
WORKDIR /data

ENTRYPOINT ["/entrypoint"]
CMD ["devpi-server"]
