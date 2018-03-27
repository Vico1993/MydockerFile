FROM ubuntu

RUN apt-get update 
RUN apt-get install apache2 -y

RUN apt-get install -y php7.0  php7.0-mysql 
RUN apt-get install -y libapache2-mod-php7.0 php7.0-mysql php7.0-curl php7.0-json

EXPOSE 80

CMD ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]
