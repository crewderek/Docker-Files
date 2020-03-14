# The goal of the docker file is to create a 7 Days to Die dedicated server
# that can run seamlessly inside of a replicatable docker container.

#Use the latest version of Ubuntu
FROM ubuntu:latest

RUN useradd -ms /bin/bash steamcmd
ADD http://media.steampowered.com/installer/steamcmd_linux.tar.gz /home/steamcmd/
RUN chown steamcmd:steamcmd /home/steamcmd/steamcmd_linux.tar.gz

#Add the steamcmd user to the container
RUN tar -xzf /home/steamcmd/steamcmd_linux.tar.gz --directory /home/steamcmd \
	&& mkdir /home/steamcmd/7DaysToDie \
	&& chown steamcmd:steamcmd /home/steamcmd/7DaysToDie \
	&& rm -rf /home/steamcmd/steamcmd_linux.tar.gz

# Run update, and install commands here
RUN apt update \
	&& apt-get install software-properties-common -y \
	&& add-apt-repository multiverse \
	&& dpkg --add-architecture i386 \
	&& apt-get update \
	&& apt install nano -y \
	&& apt install lib32gcc1 -y


USER steamcmd
WORKDIR /home/steamcmd
#RUN /bin/bash /home/steamcmd/steamcmd.sh +login anonymous +force_install_dir /home/steamcmd/7DaysToDie/ +app_update 294420


#Network ports to expose
#Game ports
EXPOSE 26900
EXPOSE 26901
EXPOSE 26902

#Web page port
EXPOSE 8080
