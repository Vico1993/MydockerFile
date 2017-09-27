FROM debian
MAINTAINER VictorPiolin ( victorpiolin@gmail.com )

# Install dependencies
RUN apt-get update && \
apt-get upgrade -y && \
apt-get install -qy wget \
                        openvpn \
                        python \
                        transmission-cli \
                        transmission-daemon

EXPOSE 9091
EXPOSE 6669/udp

# Stop daemon before setup
CMD [ "/etc/init.d/transmission-daemon", "stop" ]
CMD [ "/etc/init.d/transmission", "stop" ]

# Copy Config
COPY settings.json /var/lib/transmission/settings.json

CMD [ "/usr/bin/transmission-daemon", "-f", "-g", "/var/lib/transmission" ]

#
# docker run -d -t -i -v /home/vico/dwled:/dwled -v /home/vico/dwling:/dwling --name transtrans transmission
# docker run -d -t -i -v /Users/victorpiolin/Code/Local/docker/transmission/dwled:/dwled -v /Users/victorpiolin/Code/Local/docker/transmission/dwling:/dwling -p 127.0.0.1:9091:9091 --name trans transmission
#
