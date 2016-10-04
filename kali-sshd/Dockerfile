FROM kalilinux/kali-linux-docker
MAINTAINER hackbyday@gmail.com

RUN echo "deb http://http.kali.org/kali kali-rolling main contrib non-free" > /etc/apt/sources.list && \
echo "deb-src http://http.kali.org/kali kali-rolling main contrib non-free" >> /etc/apt/sources.list

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get -y remove dmidecode && \
    apt-get -y update && \
    apt-get -y dist-upgrade && \
    apt-get -y install openssh-server locales && \
    sed -i -e 's/^# en_AU.UTF-8/en_AU.UTF-8/' /etc/locale.gen && \
    locale-gen && \
    sed -i -e 's/^PermitRootLogin .*/PermitRootLogin yes/' /etc/ssh/sshd_config && \
    mkdir /var/run/sshd && \
    chmod 0755 /var/run/sshd && \
    echo "root:toor" | chpasswd && \
    apt-get clean

EXPOSE 22

CMD ["/usr/sbin/sshd", "-D"]
