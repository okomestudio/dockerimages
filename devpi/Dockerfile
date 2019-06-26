FROM python:3.7

ENV DEVPI_CLIENT_VERSION 4.4.0
ENV DEVPI_SERVER_VERSION 4.9.0

RUN addgroup --system --gid 1000 devpi \
 && adduser --disabled-password --system --uid 1000 \
      --home /data --shell /sbin/nologin --gid 1000 devpi

RUN pip install -q "devpi-client==$DEVPI_CLIENT_VERSION" \
 && rm -rf ~/.cache/pip
RUN pip install -q "devpi-server==$DEVPI_SERVER_VERSION" \
 && rm -rf ~/.cache/pip

VOLUME /data

COPY entrypoint /entrypoint
RUN chmod +x /entrypoint

USER devpi
ENV HOME /data
WORKDIR /data

ENTRYPOINT ["/entrypoint"]
CMD ["devpi"]
