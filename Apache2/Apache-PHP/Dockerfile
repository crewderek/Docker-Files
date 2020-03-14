#Install the ubuntu package and show the maintainer
FROM ubuntu:latest
MAINTAINER Derek Crew <derek.crew@rocky.edu>

#Install all the required packages
RUN apt-get update && apt-get -y upgrade && apt-get install -y software-properties-common && add-apt-repository ppa:ondrej/php &&  DEBIAN_FRONTEND=noninteractive apt-get -y install apache2 php7.3 libapache2-mod-php7.3 php7.3-mysql php7.3-xml && apt install -y ffmpeg && apt install -y httpie

#Create config folder and file
RUN mkdir -p /var/www/config
RUN > /var/www/config/databaseConfig.ini

#Enable apache mods
RUN a2enmod php7.3
RUN a2enmod rewrite
RUN phpenmod pdo

#Manually set up the apache2 enviroment variables
ENV APACHE_RUN_USER www-data
ENV APACHE_RUN_GRUOP www-data

CMD ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]
