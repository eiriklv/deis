FROM deis/base:latest
MAINTAINER Gabriel Monroy <gabriel@opdemand.com>

# install rsyslog from rsyslog.com
RUN echo "deb http://ubuntu.adiscon.com/v7-stable precise/" > /etc/apt/sources.list.d/rsyslog.list
RUN gpg --recv-keys --keyserver keyserver.ubuntu.com AEF0CF8E
RUN gpg --export --armor AEF0CF8E | sudo apt-key add -
RUN apt-get update
RUN apt-get install -yq rsyslog

# create /var/log/deis for holding logs (access via bind mount)
RUN mkdir -p /var/log/deis

# add the current build context to /app
ADD . /app

# prepare execution environment
WORKDIR /app
CMD ["/app/bin/boot"]
EXPOSE 514
