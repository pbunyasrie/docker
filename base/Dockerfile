### Dockerfile
#
#   See https://github.com/russmckendrick/docker

FROM centos:latest
MAINTAINER Russ McKendrick <russ@media-glass.es>
RUN rpm --import /etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7
RUN yum -y install http://dl.fedoraproject.org/pub/epel/7/x86_64/e/epel-release-7-2.noarch.rpm http://dl.iuscommunity.org/pub/ius/stable/CentOS/7/x86_64/ius-release-1.0-13.ius.centos7.noarch.rpm && yum -y update && yum -y install yum-priorities vim-enhanced && yum clean all
