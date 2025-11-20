# use Debian slim as a lightweight base
FROM debian:bookworm-slim

ENV DEBIAN_FRONTEND=noninteractive

# install Tor
RUN apt-get update && apt-get install -y --no-install-recommends \
	tor \
&& rm -rf /var/lib/apt/lists/*

# copy our Tor configuration file into place
COPY tor/torrc /etc/tor/torrc

# create the hidden-service directory (persistent via volume)
RUN mkdir -p /var/lib/tor/hidden_service \
	&& chown -R debian-tor:debian-tor /var/lib/tor && \
	chmod 700 /var/lib/tor/hidden_service

USER debian-tor

# start tor with our config file. running in the foreground
CMD ["tor", "-f", "/etc/tor/torrc"]