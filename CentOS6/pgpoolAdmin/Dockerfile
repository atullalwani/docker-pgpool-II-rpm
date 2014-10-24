# Docker file to create pgpool-II rpm

FROM centos:centos6

MAINTAINER Tatsuo Ishii <ishii@sraoss.co.jp>

ENV PGPOOL_ADMIN_VERSION 3.4beta2

RUN yum update -y
RUN yum install -y wget
RUN wget http://yum.postgresql.org/9.3/redhat/rhel-6-x86_64/pgdg-centos93-9.3-1.noarch.rpm
RUN rpm -ivh pgdg-centos93-9.3-1.noarch.rpm
RUN yum install -y postgresql93 postgresql93-server tar rpm-build
RUN yum install -y php-pgsql
ADD rpmbuild.sh /tmp/rpmbuild.sh
ADD build.sh /tmp/build.sh
CMD /tmp/build.sh