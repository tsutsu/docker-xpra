FROM ubuntu:saucy

USER root
ENV HOME /root
WORKDIR /root

RUN apt-get update
ENV DEBIAN_FRONTEND noninteractive
RUN dpkg-divert --local --rename --add /sbin/initctl && ln -sf /bin/true /sbin/initctl

RUN apt-get install -y xpra openssh-server

RUN echo X11Forwarding yes >> /etc/ssh/sshd_config
RUN echo X11DisplayOffset 10 >> /etc/ssh/sshd_config
RUN echo PermitRootLogin yes >> /etc/ssh/sshd_config
ADD start-under-xpra /usr/local/bin/start-under-xpra
ADD xpra-session /etc/X11/Xsession

RUN mkdir -p /root/.ssh && chmod 700 /root/.ssh
ADD user.id_rsa.pub /root/.ssh/authorized_keys

ENTRYPOINT ["/usr/local/bin/start-under-xpra"]
