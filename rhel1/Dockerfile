FROM registry.access.redhat.com/ubi7
MAINTAINER Veer Muchandi veer@redhat.com
ADD ./init.sh ./
RUN yum install nmap-ncat --disablerepo=* --enablerepo=ubi-7-server-extras-rpms -y && yum clean all -y
RUN yum install telnet --disablerepo=* --enablerepo=ubi-7-server-extras-rpms -y && yum clean all -y
RUN yum install net-tools --disablerepo=* --enablerepo=ubi-7-server-extras-rpms -y && yum clean all -y
RUN yum install bind-utils --disablerepo=* --enablerepo=ubi-7-server-extras-rpms -y && yum clean all -y
RUN yum install mod_ssl --disablerepo=* --enablerepo=ubi-7-server-extras-rpms -y && yum clean all -y
RUN yum install ansible --disablerepo=* --enablerepo=ubi-7-server-extras-rpms -y && yum clean all -y
RUN yum install atomic-openshift-clients --disablerepo=* --enablerepo=ubi-7-server-extras-rpms -y && yum clean all -y
RUN chown 1001:1001 init.sh && chmod o+w init.sh
USER 1001
CMD ["./init.sh"]
