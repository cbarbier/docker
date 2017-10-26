######
#EX01#
######

FROM debian
# author
MAINTAINER Cbarbier

# Update and install Vim
RUN apt -y update && apt -y install \
	wget \
	tar \
	bzip2

#open ports
EXPOSE 9987/udp
EXPOSE 30033
EXPOSE 10011
EXPOSE 41144

#add new user
RUN adduser teamspeak
WORKDIR /home/teamspeak

#get the tar ball
RUN cd /home/teamspeak
RUN wget http://dl.4players.de/ts/releases/3.0.13.8/teamspeak3-server_linux_amd64-3.0.13.8.tar.bz2
RUN tar -jxvf teamspeak3-server_linux_amd64-3.0.13.8.tar.bz2
RUN rm teamspeak3-server_linux_amd64-3.0.13.8.tar.bz2
COPY ts3server.ini /home/teamspeak/teamspeak3-server_linux_amd64/ts3server.ini
WORKDIR teamspeak3-server_linux_amd64
USER teamspeak
ENTRYPOINT ["sh", "ts3server_minimal_runscript.sh", "inifile=ts3server.ini"]

#command to execute the server
#docker run -ti -p 9987:9987/udp -p 30033:30033 -p 10011:10011 -p 41144:41144 --rm tmspk bash
