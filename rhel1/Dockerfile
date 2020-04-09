FROM registry.access.redhat.com/ubi7
ADD ./init.sh ./


RUN yum install yum-utils -y && yum clean all -y
RUN yumdownloader azure-cli
RUN rpm -ivh --nodeps azure-cli-*.rpm

# ADD ./azure-cli.repo /etc/yum.repos.d/
# RUN yum install rh-python36 -y && yum clean all -y
# RUN rpm --import https://packages.microsoft.com/keys/microsoft.asc
# RUN yum install azure-cli -y && yum clean all -y

# RUN yum install https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm -y && yum clean all -y
# RUN yum install ansible -y && yum clean all -y
# RUN yum install atomic-openshift-clients
# RUN yum install nmap-ncat -y && yum clean all -y
# RUN yum install net-tools -y && yum clean all -y
# RUN yum install bind-utils -y && yum clean all -y
# RUN yum install mod_ssl -y && yum clean all -y

RUN chown 1001:1001 init.sh && chmod o+w init.sh
USER 1001
CMD ["./init.sh"]
