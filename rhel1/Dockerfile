FROM registry.access.redhat.com/ubi8
ADD ./init.sh ./

# Install python3 for AZ CLI
RUN yum install -y python3
RUN python3 --version

# Install AZ CLI
ADD ./azure-cli.repo /etc/yum.repos.d/
RUN rpm --import https://packages.microsoft.com/keys/microsoft.asc
RUN yum install azure-cli -y && yum clean all -y

RUN yum install ansible -y && yum clean all -y
RUN yum install atomic-openshift-clients
RUN yum install nmap-ncat -y && yum clean all -y
RUN yum install net-tools -y && yum clean all -y
RUN yum install bind-utils -y && yum clean all -y
RUN yum install mod_ssl -y && yum clean all -y

RUN chown 1001:1001 init.sh && chmod o+w init.sh
USER 1001
ENV HOME=/tmp/
CMD ["./init.sh"]
