FROM registry.access.redhat.com/ubi7
MAINTAINER Veer Muchandi veer@redhat.com
ADD ./init.sh ./
# RUN yum install nmap-ncat -y && yum clean all -y
# RUN yum install net-tools -y && yum clean all -y
# RUN yum install bind-utils -y && yum clean all -y
# RUN yum install mod_ssl -y && yum clean all -y
ENV ANSIBLE_VERSION=2.8.2
RUN INSTALL_PKGS="rh-python36-python-pip" && \
    DISABLE_REPOS=--disablerepo='rhel-*' && \
    yum $DISABLE_REPOS install -y $INSTALL_PKGS && \
    source scl_source enable rh-python36 && \
    scl enable rh-python36 bash && \
    python3 -m pip install ansible==$ANSIBLE_VERSION paramiko && \
    yum $DISABLE_REPOS clean all -y && \
    rm -rf /var/cache/yum
RUN chown 1001:1001 init.sh && chmod o+w init.sh
USER 1001
CMD ["./init.sh"]
