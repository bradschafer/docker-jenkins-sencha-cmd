FROM jenkins

MAINTAINER Maximiliano Fierro <elmasse@gmail.com>

USER root


# Install openjdk8 and ruby
RUN apt-get update && \
    apt-get install -y openjdk-8-jre unzip

#Accept arguments for the command version 
ARG cmd=6.5.0.180


RUN wget http://cdn.sencha.com/cmd/${cmd}/no-jre/SenchaCmd-${cmd}-linux-amd64.sh.zip -O senchacmd.zip && unzip senchacmd.zip && rm senchacmd.zip && chmod +x SenchaCmd-${cmd}-linux-amd64.sh
RUN ./SenchaCmd-${cmd}-linux-amd64.sh -q -dir /opt/Sencha/Cmd/${cmd} -Dall=true
RUN rm SenchaCmd-${cmd}-linux-amd64.sh && chmod +x /opt/Sencha/Cmd/${cmd}/sencha


RUN apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN chown -R jenkins:jenkins /opt/Sencha/Cmd/${cmd}/sencha

ENV PATH /opt/Sencha/Cmd/${cmd}/sencha:$PATH

USER jenkins


COPY plugins.txt /usr/share/jenkins/plugins.txt
RUN /usr/local/bin/plugins.sh /usr/share/jenkins/plugins.txt
