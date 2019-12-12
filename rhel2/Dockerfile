FROM registry.access.redhat.com/rhel7/rhel-atomic
ADD ./init.sh ./
RUN microdnf install -y
RUN microdnf telnet -y
RUN microdnf net-tools -y
RUN microdnf bind-utils -y
RUN microdnf mod_ssl -y
RUN microdnf ansible -y
RUN microdnf atomic-openshift-clients -y
RUN chown 1001:1001 init.sh && chmod o+w init.sh
USER 1001
CMD ["./init.sh"]
