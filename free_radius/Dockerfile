# Use a ubuntu parent image
FROM ubuntu

# Install any needed packages
RUN apt-get update

RUN apt-get install freeradius --yes

RUN apt-get install iproute2 --yes

RUN cp /etc/freeradius/3.0/mods-config/files/authorize /etc/freeradius/3.0/mods-config/files/authorize.original
RUN cp /etc/freeradius/3.0/clients.conf /etc/freeradius/3.0/clients.conf.original

RUN chown freerad:freerad /etc/freeradius/3.0/clients.conf
RUN chmod 640 /etc/freeradius/3.0/clients.conf

RUN chown freerad:freerad /etc/freeradius/3.0/mods-config/files/authorize
RUN chmod 640 /etc/freeradius/3.0/mods-config/files/authorize

COPY authorize /etc/freeradius/3.0/mods-config/files/
COPY clients.conf /etc/freeradius/3.0/

