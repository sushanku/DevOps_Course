# Our base image
FROM ubuntu/apache2

# make dir infosys for our resources to live
RUN mkdir /var/www/infosys

# copy our resources
COPY index.html /var/www/infosys

# copy our virtual hosts
COPY infosys.conf /etc/apache2/sites-available/infosys.conf

# enable our virtual hosts
RUN a2ensite infosys.conf && a2dissite 000-default.conf

# Expose port 80
EXPOSE 80

# Start Apache in the foreground
CMD ["apachectl", "-D", "FOREGROUND"]