FROM debian:stretch-slim

RUN apt-get update \
 && apt-get install -y --no-install-recommends \
      ca-certificates \
      build-essential \
      wget \
 && rm -rf /var/lib/apt/lists/*

RUN wget https://github.com/google/leveldb/archive/v1.20.tar.gz \
 && tar -zxvf v1.20.tar.gz -C /usr/local/src/ \
 && cd /usr/local/src/leveldb-1.20 \
 && make \
 && cp -r out-static/lib* out-shared/lib* /usr/local/lib/ \
 && cp -r include/leveldb /usr/local/include/ \
 && ldconfig

CMD /bin/sh
