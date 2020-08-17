FROM jenkins/jenkins:lts
USER root

COPY ./sources.list /etc/apt/sources.list
RUN apt-get update 
RUN apt-get install -y apt-transport-https ca-certificates curl gnupg2 software-properties-common sudo 
RUN curl -fsSL https://download.docker.com/linux/debian/gpg | apt-key add -
RUN apt-get update 
RUN curl -fsSL https://get.docker.com | bash -s docker --mirror Aliyun
RUN rm -rf /var/lib/apt/lists/*

RUN echo "jenkins ALL=NOPASSWD: ALL" >> /etc/sudoers

RUN curl -L https://get.daocloud.io/docker/compose/releases/download/1.24.0/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose
RUN chmod +x /usr/local/bin/docker-compose
USER jenkins

COPY ./plugins.txt /usr/share/jenkins/plugins.txt
RUN /usr/local/bin/plugins.sh /usr/share/jenkins/plugins.txt
