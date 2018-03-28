FROM couchdb:2.1.1

RUN apt-get update -y -qq && apt-get install -y --no-install-recommends apt-transport-https

RUN curl -sL https://deb.nodesource.com/setup_8.x | bash -

RUN apt-get install -y --no-install-recommends \
    nodejs \
  && rm -rf /var/lib/apt/lists/*

COPY couch_ws.ini /opt/couchdb/etc/local.d/couch_ws.ini

RUN mkdir /opt/couch_ws

COPY package.json /opt/couch_ws
COPY couch_ws.js /opt/couch_ws

RUN cd /opt/couch_ws && npm i

EXPOSE  8888
