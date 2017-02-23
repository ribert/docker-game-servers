FROM centos:latest

RUN yum install -y wget glibc.i686 libstdc++.i686 vim

COPY steamcmd ./steamcmd
WORKDIR /steamcmd
RUN ./steamcmd.sh +login anonymous +force_install_dir /tf2server/ +app_update 232250 validate +exit 

WORKDIR /tf2server
RUN mkdir -p /root/.steam/sdk32/
COPY steamclient.so /root/.steam/sdk32/steamclient.so

CMD ./srcds_run -game tf -strictportbind +ip 0.0.0.0 -port 27010 +port 27000 +map pl_badwater -maxplayers 32
