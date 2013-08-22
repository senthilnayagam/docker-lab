FROM base

RUN apt-get update
RUN apt-get install -y --force-yes build-essential curl git vim
RUN apt-get install -y --force-yes openssh-server openssh-client
RUN apt-get clean

# workaround
RUN dpkg-divert --local --rename --add /sbin/initctl
RUN ln -fs /bin/true /sbin/initctl

# create user
RUN useradd monitorel
RUN mkdir -p /home/monitorel/.ssh; chown monitorel /home/monitorel/.ssh; chmod 700 /home/monitorel/.ssh
ADD ./ssh/authorized_keys /home/monitorel/.ssh/
RUN chown monitorel /home/monitorel/.ssh/authorized_keys; chmod 600 /home/monitorel/.ssh/authorized_keys

# setup sudoers
RUN echo 'monitorel ALL=(ALL)   NOPASSWD:ALL' >> /etc/sudoers.d/monitorel

## setup sshd and generate ssh-keys by init script
#ADD sshd_config /etc/ssh/sshd_config
RUN mkdir /var/run/sshd
RUN /etc/init.d/ssh start
RUN /etc/init.d/ssh stop

EXPOSE 22
# EXPOSE 49222:22

CMD ["/usr/sbin/sshd", "-D"]
