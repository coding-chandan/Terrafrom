# Use a specific Ubuntu version
FROM ubuntu:22.04

# Update apt sources to use valid mirrors
RUN sed -i 's|http://ports.ubuntu.com|http://archive.ubuntu.com|g' /etc/apt/sources.list && \
    apt-get update && \
    apt-get install -y apache2 apache2-utils zip unzip curl  && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# Set the working directory
WORKDIR /var/www/html

# Download the website zip file
RUN curl -o carvilla.zip https://www.free-css.com/assets/files/free-css-templates/download/page296/carvilla.zip

# Unzip the downloaded file
RUN unzip carvilla.zip && \
    cp -rvf carvilla-v1.0/* . && \
    rm -rf carvilla-v1.0 carvilla.zip

# Expose port 80 for web traffic
EXPOSE 80

# Start the Apache web server
CMD ["apachectl", "-D", "FOREGROUND"]
