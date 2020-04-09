FROM registry.access.redhat.com/ubi7
ADD ./init.sh ./

RUN yum install https://dl.fedoraproject.org/pub/epel/epel-release-latest-$(rpm -E '%{rhel}').noarch.rpm -y
#RUN yum install https://centos7.iuscommunity.org/ius-release.rpm -y
#RUN yum install -y python36u python36u-pip
RUN yum list | grep python3
RUN yum install -y python36 && yum clean all -y

ADD ./azure-cli.repo /etc/yum.repos.d/
RUN yum install rh-python36 -y && yum clean all -y
RUN rpm --import https://packages.microsoft.com/keys/microsoft.asc
RUN yum install azure-cli -y && yum clean all -y

# RUN yum install ansible -y && yum clean all -y
# RUN yum install atomic-openshift-clients
# RUN yum install nmap-ncat -y && yum clean all -y
# RUN yum install net-tools -y && yum clean all -y
# RUN yum install bind-utils -y && yum clean all -y
# RUN yum install mod_ssl -y && yum clean all -y

RUN chown 1001:1001 init.sh && chmod o+w init.sh
USER 1001
CMD ["./init.sh"]
