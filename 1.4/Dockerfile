FROM ubuntu

RUN apt-get update && apt-get install -y curl

WORKDIR /srv
COPY curler.sh /srv/
CMD sh curler.sh