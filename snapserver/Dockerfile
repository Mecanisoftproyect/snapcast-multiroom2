FROM debian:11

ARG  snapcast_version=0.27.0
ENV  STREAM_NAME Snapserver

RUN  apt-get update \
  && apt-get install -y wget ca-certificates 
  
RUN  wget https://github.com/badaix/snapcast/releases/download/v${snapcast_version}/snapserver_${snapcast_version}-1_amd64.deb
RUN  dpkg -i snapserver_${snapcast_version}-1_amd64.deb \
  ;  apt-get update \
  && apt-get -f install -y \
  && rm -rf /var/lib/apt/lists/*
RUN dpkg -i snapserver_${snapcast_version}-1_amd64.deb
RUN snapserver -v
RUN mkdir /fifo
COPY snapserver.conf /etc/snapserver
EXPOSE 1704 1705
#ENTRYPOINT ["/bin/bash","-c","source /etc/default/snapserver && snapserver $SNAPSERVER_OPTS"]
ENTRYPOINT ["snapserver"]
