FROM debian:bullseye

RUN apt-get update && apt-get upgrade -y &&\
	apt-get install -y nginx openssl

RUN mkdir -p /etc/nginx/ssl

RUN openssl req -x509 -nodes -out /etc/nginx/ssl/inception.crt -keyout \
	/etc/nginx/ssl/inception.key -subj "/C=FR/ST=ARA/L=LYON/O=42/OU=42/CN=avialle-.42.fr/UID=avialle-42"

COPY /conf/nginx.conf /etc/nginx/nginx.conf

RUN mkdir -p /var/www/wordpress &&\
	chown -R www-data:www-data /var/www/wordpress

CMD ["nginx", "-g", "daemon off;"]