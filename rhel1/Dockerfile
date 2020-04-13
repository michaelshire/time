FROM registry.access.redhat.com/ubi8
ADD ./init.sh ./
ENV HOME=/tmp/

# Install python3 for AZ CLI and ansible
RUN yum install -y python3 python3-virtualenv python3-pip
RUN python3 --version

# Install AZ CLI
ADD ./azure-cli.repo /etc/yum.repos.d/
RUN rpm --import https://packages.microsoft.com/keys/microsoft.asc
RUN yum install azure-cli -y && yum clean all -y
RUN az --version

# Install Ansible
RUN pip3 install --user ansible
RUN ansible --version

# Install other tools
RUN yum install atomic-openshift-clients
RUN yum install nmap-ncat -y && yum clean all -y
RUN yum install net-tools -y && yum clean all -y
RUN yum install bind-utils -y && yum clean all -y
RUN yum install mod_ssl -y && yum clean all -y

RUN chown 1001:1001 init.sh && chmod o+w init.sh
USER 1001

CMD ["./init.sh"]
