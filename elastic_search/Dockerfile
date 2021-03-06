# Use a ubuntu parent image
FROM ubuntu:20.04

# Install any needed packages
RUN apt-get update --fix-missing


# Install dependencies needed to import elesaticsearch GPG key
RUN apt-get install apt-transport-https
RUN apt-get install wget -y
RUN apt-get install gnupg -y

# Import elastic search GPG key
RUN wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | apt-key add -

# Install dependency to add elastic apt repository
RUN apt-get install software-properties-common -y

# Add elastic apt repository
RUN add-apt-repository "deb https://artifacts.elastic.co/packages/7.x/apt stable main"

# Update package repository indices
RUN apt-get update

# Install elasticsearch
RUN apt-get install elasticsearch

# Backup original elasticsearch configuration file
RUN cp /etc/elasticsearch/elasticsearch.yml /etc/elasticsearch/elasticsearch.yml.original

# Copy required elasticsearch configuration file into docker container
COPY elasticsearch.yml /etc/elasticsearch

# Install systemd for systemctl
RUN apt-get install systemd -y

# Add elasticsearch service to startup
RUN systemctl enable elasticsearch

# Expose the necessary ports
EXPOSE 9200 9300

# Switch user
USER elasticsearch

# Add the elastic search binary location to the PATH variable
ENV PATH=$PATH:/usr/share/elasticsearch/bin

# Start elasticsearch
ENTRYPOINT elasticsearch

