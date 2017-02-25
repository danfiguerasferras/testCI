# From the php fpm image
FROM ubuntu:xenial
# We update the repositories
RUN apt-get update

# We install nginx, nano, etc
RUN apt-get install -y php7.0 php7.0-fpm nginx nano curl net-tools ssh

# We have to allow local connections to the machine
RUN sed -i 's/;listen.allowed_clients = 127.0.0.1/listen.allowed_clients = 127.0.0.1/g' /etc/php/7.0/fpm/pool.d/www.conf
# We start the php fpm, or the socket will not be created

ADD auxiliar/default /etc/nginx/sites-available/
RUN echo "<?php echo 'Ola k ase';" >> /var/www/html/index.php

# Expose the port and starts the nginx
EXPOSE 80


# Remember to put it in the gitlab-ci.yml, otherwise it won't work anyway
CMD service php7.0-fpm start
CMD service nginx start
