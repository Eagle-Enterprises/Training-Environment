FROM ghcr.io/epicgames/unreal-engine:dev-4.27 AS builder

COPY --chown=ue4:ue4 . /tmp/project

RUN sudo apt-get install python3 python3-dev python3-pip

RUN sudo pip3 install --upgrade pip && sudo pip3 install ue4cli

WORKDIR /home/

RUN sudo sudo git clone https://github.com/Microsoft/AirSim.git
RUN sudo bash AirSim/setup.sh
RUN sudo bash AirSim/build.sh
RUN sudo cp /tmp/project/Source/BlocksServer.Target* /home/AirSim/Unreal/Environments/Blocks/Source

WORKDIR /home/AirSim/Unreal/Environments/Blocks/

RUN sudo ue4 setroot /home/ue4/UnrealEngine
RUN sudo ue4 package Development -server -noclient

FROM adamrehn/ue4-runtime:latest
COPY --from=builder --chown=ue4:ue4 /home/AirSim/Unreal/Environments/Blocks/LinuxServer /home/ue4/project

EXPOSE 7777/udp
EXPOSE 7777/tcp

ENTRYPOINT [ "/home/ue4/project/VsServer.sh", "-log" ]