FROM centos:7

ADD cloudera-cm5.repo /etc/yum.repos.d/cloudera-cm5.repo

RUN mkdir -p /repo
# disable ssl verification by yum if behind proxy
RUN if [ \"$HTTP_PROXY\" != "" ]; then echo 'sslverify=0' >> /etc/yum.conf ; fi

WORKDIR /repo

RUN yum -y install yum-utils createrepo
RUN reposync -r cloudera-cm5
WORKDIR /repo/cloudera-cm5
RUN createrepo .
