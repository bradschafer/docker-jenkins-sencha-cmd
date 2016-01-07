FROM jenkins

MAINTAINER Maximiliano Fierro <elmasse@gmail.com>

USER root

# Install openjdk7 and ruby
RUN apt-get update && \
    apt-get install -y openjdk-7-jre ruby2.0 unzip

#6.0.2.14
#6.0.0.202

RUN curl -o /cmd.sh.zip http://cdn.sencha.com/cmd/6.0.2.14/no-jre/SenchaCmd-6.0.2.14-linux-amd64.sh.zip && \
    unzip -p /cmd.sh.zip > /cmd-install.sh && \
    chmod +x /cmd-install.sh && \
    /cmd-install.sh -q -dir "/opt/sencha-cmd/Cmd/6.0.2.14" && \
    rm /cmd-install.sh /cmd.sh.zip

RUN apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN chown -R jenkins:jenkins /opt/sencha-cmd

ENV PATH /opt/sencha-cmd/Cmd/6.0.2.14:$PATH

USER jenkins


COPY plugins.txt /usr/share/jenkins/plugins.txt
RUN /usr/local/bin/plugins.sh /usr/share/jenkins/plugins.txt