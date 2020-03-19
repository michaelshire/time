FROM registry.access.redhat.com/ubi7
MAINTAINER Veer Muchandi veer@redhat.com
ADD ./init.sh ./
RUN yum install https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm -y && yum clean all -y
RUN yum install ansible
# RUN yum install nmap-ncat -y && yum clean all -y
# RUN yum install net-tools -y && yum clean all -y
# RUN yum install bind-utils -y && yum clean all -y
# RUN yum install mod_ssl -y && yum clean all -y
# RUN chown 1001:1001 init.sh && chmod o+w init.sh
USER 1001
CMD ["./init.sh"]
