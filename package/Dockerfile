FROM ghcr.io/verrazzano/golang:v1.20.12 as build
RUN yum update -y \
    && yum clean all \
    && rm -rf /var/cache/yum/*
COPY bin/backup-restore-operator /usr/bin/
RUN mkdir -p /licenses
COPY LICENSE README.md THIRD_PARTY_LICENSES.txt SECURITY.md /licenses/
ENTRYPOINT ["backup-restore-operator"]
