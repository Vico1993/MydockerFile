FROM debian
MAINTAINER VictorPiolin ( victorpiolin@gmail.com )

# Install dependencies
RUN apt-get update && \
apt-get upgrade -y && \
apt-get install python-pip python-dev git-core libssl-dev libxslt1-dev libxslt1.1 libxml2-dev libxml2 libssl-dev libffi-dev build-essential wget -y && \

wget http://rarlab.com/rar/unrarsrc-5.2.7.tar.gz && \
tar -xvf unrarsrc-5.2.7.tar.gz && \
cd unrar && \
make -f makefile && \
install -v -m755 unrar /usr/bin && \

# Install OpenSSL
pip install pyopenssl && \

# Install SickRage
git clone https://github.com/SickRageTV/SickRage.git /opt/sickrage && \
chown -R root:root /opt/sickrage && \
pip install --user -U -r /opt/sickrage/requirements.txt

# Downloads directory
VOLUME /downloads

# Media directory
VOLUME /media

EXPOSE 8081

CMD [ "cp", "-v", "/opt/sickrage/runscripts/init.debian", "/etc/init.d/sickrage" ]
CMD [ "chown", "root:root", "/etc/init.d/sickrage" ]
CMD [ "chmod", "644", "/etc/init.d/sickrage" ]

CMD [ "service", "sickrage", "start" ]

#GO
# RUN python /opt/sickrage/SickBeard.py -d >> /home/debug.txt
# CMD [ "/usr/bin/python", "/opt/sickrage/SickBeard.py", "--datadir=/config", "--config=/config/config.ini" ]

##
## docker run -p 127.0.0.1:8081:8081 -v /Users/victorpiolin/Code/Local/docker/sickrage/media:/media -v /Users/victorpiolin/Code/Local/docker/sickrage/dowload:/downloads --name sicksick -d -ti sickrage
##
