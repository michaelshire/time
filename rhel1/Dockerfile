FROM registry.access.redhat.com/ubi7
MAINTAINER Veer Muchandi veer@redhat.com
ADD ./init.sh ./
RUN yum install nmap-ncat --disablerepo=* -y && yum clean all -y
RUN yum install telnet --disablerepo=* -y && yum clean all -y
RUN yum install net-tools --disablerepo=* -y && yum clean all -y
RUN yum install bind-utils --disablerepo=* -y && yum clean all -y
RUN yum install mod_ssl --disablerepo=* -y && yum clean all -y
RUN yum install ansible --disablerepo=* -y && yum clean all -y
RUN yum install atomic-openshift-clients -y && yum clean all -y
RUN chown 1001:1001 init.sh && chmod o+w init.sh
USER 1001
CMD ["./init.sh"]
