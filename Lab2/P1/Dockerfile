FROM ubuntu

RUN  apt update -y
RUN  apt install nginx -y

EXPOSE 80

COPY templete.html  /var/www/html
ADD tarfile.tar.gz   /var/www/html

CMD ["nginx", "-g", "daemon off;"]














