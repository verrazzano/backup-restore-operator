FROM ghcr.io/oracle/oraclelinux:7-slim
RUN yum update -y \
    && yum clean all \
    && rm -rf /var/cache/yum/*
COPY bin/backup-restore-operator /usr/bin/
mkdir -p /licenses
COPY LICENSE README.md THIRD_PARTY_LICENSES.txt SECURITY.md /licenses/
ENTRYPOINT ["backup-restore-operator"]
