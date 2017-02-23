FROM centos:latest

RUN yum install -y wget glibc.i686 libstdc++.i686 vim

COPY steamcmd ./steamcmd
WORKDIR /steamcmd
RUN ./steamcmd.sh +login anonymous +force_install_dir /csserver/ +app_set_config 90 mod cstrike +app_update 90 validate +app_update 90 -beta beta validate +exit

WORKDIR /csserver
COPY addons ./cstrike/addons
COPY server.cfg ./cstrike/server.cfg
RUN mkdir -p /root/.steam/sdk32/ && \
    cp cstrike/addons/metamod/dlls/metamod.so ~/.steam/sdk32/steamclient.so
COPY maps/* cstrike/maps/
COPY maps/maps/sound/de_torn/ cstrike/maps/sound/de_torn/
COPY maps/maps/gfx/env/* cstrike/maps/gfx/env/
COPY liblist.gam ./cstrike
COPY gungame/sound/gungame/ cstrike/sounds/gungame/

CMD ./hlds_run -game cstrike -strictportbind +ip 0.0.0.0 -port 27012 +port 27002 +map gg_capture -maxplayers 18 -insecure
#RUN ./hlds_run -console -game cstrike +port 27020 +de_dust2 +maxplayers 32 -pingboost 1
