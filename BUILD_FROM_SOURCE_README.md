# Build Instructions

The base tag this release is branched from is `v2.1.3`

Create Environment Variables

```
export DOCKER_REPO=<Docker Repository>
export DOCKER_NAMESPACE=<Docker Namespace>
export DOCKER_TAG=v2.1.3-BFS
```

Build and Push Images

```
# Build and push Rancher Backup Operator
git tag -d v2.1.3
git tag  v2.1.3
make
docker tag rancher/backup-restore-operator:v2.1.3 ${DOCKER_REPO}/${DOCKER_NAMESPACE}/rancher-backup-restore-operator:${DOCKER_TAG}
docker push ${DOCKER_REPO}/${DOCKER_NAMESPACE}/rancher-backup-restore-operator:${DOCKER_TAG}
```