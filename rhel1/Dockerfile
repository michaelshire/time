FROM registry.access.redhat.com/ubi7
MAINTAINER Veer Muchandi veer@redhat.com
ADD ./init.sh ./
# RUN yum install nmap-ncat -y && yum clean all -y
# RUN yum install net-tools -y && yum clean all -y
# RUN yum install bind-utils -y && yum clean all -y
# RUN yum install mod_ssl -y && yum clean all -y
RUN subscription-manager repos --enable rhel-7-server-ansible-2.9-rpms
RUN yum install ansible -y && yum clean all -y
RUN chown 1001:1001 init.sh && chmod o+w init.sh
USER 1001
CMD ["./init.sh"]
