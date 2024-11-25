FROM ubuntu

# Set the working directory to /home/ubuntu.
# Every command after this will be executed in this directory.
WORKDIR /home/ubuntu

# Install SSH
RUN apt update && apt-get install -y openssh-server ssh && rm -rf /var/lib/apt/lists/*

# Configure SSH
RUN mkdir /var/run/sshd

# Open port 22 to allow SSH into the container
EXPOSE 22

# Usage ssh : ssh <user>@<nom du container>
# We set user as "ubuntu" and password as "password"
RUN echo 'ubuntu:password' | chpasswd

# Start SSH server
CMD ["/usr/sbin/sshd", "-D"]