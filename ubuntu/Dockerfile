FROM ubuntu:18.04
RUN apt-get update \
    && apt-get install software-properties-common -y \
    && apt-get install openssh-server -y \
    && apt-get install sudo \
    && apt-get install -y python3-pip python3-dev \
    && cd /usr/local/bin \
    && ln -s /usr/bin/python3 python \
    && pip3 install --upgrade pip 

RUN useradd -m ansible -s /bin/bash && echo "ansible:password1" | chpasswd && usermod -aG sudo ansible 
RUN mkdir /shared && mkdir /config && mkdir /home/ansible/.ssh \
    && echo "ansible ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/ansible
# Add a /shared volume
VOLUME ["/shared"]

WORKDIR /var/ans

ENTRYPOINT service ssh restart && tail -F anything
