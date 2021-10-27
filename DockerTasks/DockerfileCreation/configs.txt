FROM ubuntu 
RUN apt update -y 
#RUN apt install -y sed
ENV DEBIAN_FRONTEND=noninteractive
#ENV TZ=Africa/Cairo
#RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone
RUN apt install apache2 -y 
RUN apt install apache2-utils -y 
RUN apt-get clean 
RUN sed -i "s/Listen 80/Listen 3004/g" /etc/apache2/ports.conf
EXPOSE 3004
CMD apachectl -D FOREGROUND


