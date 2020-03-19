FROM registry.access.redhat.com/ubi7

ENV ANSIBLE_VERSION=2.8.2

ADD ./init.sh ./
ADD ubi.repo /etc/yum.repos.d/ubi.repo

RUN yum install nmap-ncat -y && yum clean all -y
RUN yum install net-tools -y && yum clean all -y
RUN yum install bind-utils -y && yum clean all -y
RUN yum install mod_ssl -y && yum clean all -y
RUN INSTALL_PKGS="rh-python36-python-pip" && \
    DISABLE_REPOS=--disablerepo='rhel-*' && \
    yum $DISABLE_REPOS install -y $INSTALL_PKGS && \
    source scl_source enable rh-python36 && \
    scl enable rh-python36 bash && \
    python3 -m pip install ansible==$ANSIBLE_VERSION paramiko && \
    yum $DISABLE_REPOS clean all -y && \
    rm -rf /var/cache/yum
# ADD scl_enable /usr/share/container-scripts/
# ENV BASH_ENV=/usr/share/container-scripts/scl_enable \
#    ENV=/usr/share/container-scripts/scl_enable \
#    PROMPT_COMMAND="./usr/share/container-scripts/scl_enable"
RUN chown 1001:1001 init.sh && chmod o+w init.sh
USER 1001
CMD ["./init.sh"]
