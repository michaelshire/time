FROM registry.redhat.io/ubi8:latest
ADD ./init.sh ./
ENV HOME=/tmp/

# RUN yum module enable -y container-tools:1.0
# RUN yum module install -y container-tools:1.0

RUN yum install yum-utils -y
# RUN yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
# RUN yum-config-manager repos --enable=rhel-8-for-x86_64-baseos-rpms
# RUN yum-config-manager repos --enable=rhel-8-for-x86_64-appstream-rpms
#RUN yum update -y

# Install container tools
# RUN yum install podman skopeo buildah -y
# RUN yum install docker-ce-cli -y

# RUN yum install watch -y

RUN yum install wget -y
# RUN yum install wget -y && yum clean all -y
# RUN wget -O /dev/null http://speedtest.wdc01.softlayer.com/downloads/test10.zip

# Install kubeseal
RUN wget https://github.com/bitnami-labs/sealed-secrets/releases/download/v0.15.0/kubeseal-linux-amd64 -O /usr/local/bin/kubeseal
RUN chmod 755 /usr/local/bin/kubeseal

# Install git
RUN yum install -y git
# RUN yum install -y git && yum clean all -y
# RUN git --version

# Install python3 for AZ CLI and ansible
RUN yum install -y python3 python3-virtualenv python3-pip
#RUN yum install -y python3 python3-virtualenv python3-pip && yum clean all -y
# RUN python3 --version

# Install Ansible
# RUN pip3 install ansible[azure]
# RUN ansible --version
# RUN chmod -R 777 /tmp/.ansible

# Install AZ CLI
ADD ./azure-cli.repo /etc/yum.repos.d/
RUN rpm --import https://packages.microsoft.com/keys/microsoft.asc
RUN yum install azure-cli -y
# RUN yum install azure-cli -y && yum clean all -y
RUN az --version
RUN chmod -R 777 /tmp/.azure

# Install helm 2
# RUN wget -q https://get.helm.sh/helm-v2.16.7-linux-amd64.tar.gz
# RUN tar -xvf ./helm-v2.16.7-linux-amd64.tar.gz -C /tmp/
# RUN mv /tmp/linux-amd64/helm /usr/local/bin/helm
# RUN chmod 755 /usr/local/bin/helm
# RUN chmod -R 777 /tmp/.cache


# Install helm 3
RUN wget -q https://mirror.openshift.com/pub/openshift-v4/clients/helm/latest/helm-linux-amd64 -O /usr/local/bin/helm
RUN chmod 755 /usr/local/bin/helm
# RUN chmod -R 777 /tmp/.cache

# Install OC CLI
RUN wget -q https://mirror.openshift.com/pub/openshift-v4/clients/oc/4.5/linux/oc.tar.gz
RUN tar -xzf ./oc.tar.gz -C /usr/local/bin/
RUN chmod 755 /usr/local/bin/oc
RUN oc version
RUN yum install iputils -y
RUN yum install nmap-ncat -y
RUN yum install net-tools -y
RUN yum install bind-utils -y
RUN yum install mod_ssl -y
RUN yum install openssl -y && yum clean all -y
# RUN yum install nmap-ncat -y && yum clean all -y
# RUN yum install net-tools -y && yum clean all -y
# RUN yum install bind-utils -y && yum clean all -y
# RUN yum install mod_ssl -y && yum clean all -y

RUN chown 1001:1001 init.sh && chmod o+w init.sh
USER 1001

CMD ["./init.sh"]
