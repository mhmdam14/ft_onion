# start from a small ubuntu base image
FROM ubuntu:24.04

# prevent prompts during apt install
ENV DEBIAN_FRONTEND=noninteractive

# install openSSH server and basic certificates
RUN apt-get update && apt-get install -y --no-install-recommends \ 
	openssh-server ca-certificates tzdata \
&& rm -rf /var/lib/apt/lists/*

# create a dedicated user (svcuser) for SSH logins
RUN useradd --create-home --shell /bin/bash svcuser

# create SSH runtime directories and set proper ownership
RUN mkdir -p /var/run/sshd /home/svcuser/.ssh \
	&& chown svcuser:svcuser /home/svcuser /home/svcuser/.ssh

# copy our hardened SSH config file
COPY ssh/sshd_config /etc/ssh/sshd_config

# default command runs SSH server in foreground (-D) and logs to stderr (-e)
CMD ["/usr/sbin/sshd", "-D", "-e"]