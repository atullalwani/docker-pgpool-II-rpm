# Docker file to create pgpool-II rpm

FROM centos:centos7

MAINTAINER Bo Peng <pengbo@sraoss.co.jp>

ENV PGPOOL_VERSION 3.4.14

RUN yum install -y deltarpm
RUN yum update -y; exit 0
RUN yum install -y tar rpm-build pam-devel gcc git openssl-devel \
    libmemcached-devel wget make jade libxslt docbook-dtds docbook-style-xsl docbook-style-dsssl docbook docbook-dsssl docbook-sgml docbook-xsl openjade

RUN sed -i -e 's/^SGMLDECL "docbook.dcl"/  -- SGMLDECL "docbook.dcl" --/' /usr/share/sgml/docbook/sgml-dtd-*/catalog

# this is neccessary for "su postgres"
RUN rpm -Uvh http://yum.postgresql.org/9.4/redhat/rhel-7-x86_64/pgdg-redhat94-9.4-3.noarch.rpm
RUN yum install -y postgresql94-server

RUN su -c 'cd /var/lib/pgsql && git clone http://git.postgresql.org/git/pgpool2.git' postgres

# download pgpool-II tar ball
RUN wget http://www.pgpool.net/download.php?f=pgpool-II-$PGPOOL_VERSION.tar.gz -O /tmp/pgpool-II-$PGPOOL_VERSION.tar.gz

ADD rpmbuild.sh /tmp/
ADD build.sh /tmp/
CMD /tmp/build.sh
