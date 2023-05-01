FROM ghcr.io/oracle/oraclelinux:7-slim
RUN yum update -y \
    && yum clean all \
    && rm -rf /var/cache/yum/*
COPY bin/backup-restore-operator /usr/bin/
ENTRYPOINT ["backup-restore-operator"]
