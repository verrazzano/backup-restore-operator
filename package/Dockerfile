FROM ghcr.io/verrazzano/golang:v1.20.12 as build

COPY . /go/src/github.com/backup-restore-operator/

RUN dnf config-manager --enable ol8_appstream && \
    dnf install -y git && \
    cd /go/src/github.com/backup-restore-operator/scripts && \
    ./build && \ 
    ./test

FROM ghcr.io/oracle/oraclelinux:8-slim

RUN microdnf -y update && \
    microdnf -y clean all

COPY --from=build /go/src/github.com/backup-restore-operator/bin/backup-restore-operator /usr/bin/

RUN mkdir -p /licenses

COPY --from=build /go/src/github.com/backup-restore-operator/LICENSE /licenses/
COPY --from=build /go/src/github.com/backup-restore-operator/README.md /licenses/
COPY --from=build /go/src/github.com/backup-restore-operator/THIRD_PARTY_LICENSES.txt /licenses/

ENTRYPOINT ["backup-restore-operator"]
