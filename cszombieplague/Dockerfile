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
COPY liblist.gam ./cstrike

# Zombie Plague Resources
COPY zp_resources/models/player/zombie_source/ ./cstrike/models/player/zombie_source/
COPY zp_resources/models/zombie_plague/ ./cstrike/models/zombie_plague/
COPY zp_resources/sound/warcraft3/ ./cstrike/sound/warcraft3/
COPY zp_resources/sound/zombie_plague/ ./cstrike/sound/zombie_plague/
COPY zp_resources/sprites/flame.spr ./cstrike/sprites/flame.spr

CMD ./hlds_run -game cstrike -strictportbind +ip 0.0.0.0 -port 27013 +port 27003 +map de_dust -maxplayers 6
#RUN ./hlds_run -console -game cstrike +port 27020 +de_dust2 +maxplayers 32 -pingboost 1
