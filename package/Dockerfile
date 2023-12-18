FROM ghcr.io/verrazzano/golang:v1.20.12 as build

RUN yum update -y \
    && yum clean all \
    && rm -rf /var/cache/yum/*

COPY . /go/src/github.com/backup-restore-operator/
RUN ./build

FROM ghcr.io/verrazzano/golang:v1.20.12

COPY --from=build /go/src/github.com/backup-restore-operator/bin/backup-restore-operator /usr/bin/

RUN mkdir -p /licenses

COPY --from=build /go/src/github.com/backup-restore-operator/LICENSE /licenses/
COPY --from=build /go/src/github.com/backup-restore-operator/README.md /licenses/
COPY --from=build /go/src/github.com/backup-restore-operator/THIRD_PARTY_LICENSES.txt /licenses/

ENTRYPOINT ["backup-restore-operator"]
