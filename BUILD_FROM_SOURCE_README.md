# Build Instructions

The base tag this release is branched from is `v3.1.0`

Create Environment Variables

```
export DOCKER_REPO=<Docker Repository>
export DOCKER_NAMESPACE=<Docker Namespace>
export DOCKER_TAG=v3.1.0-BFS
```

Build and Push Images

```
# Build and push Rancher Backup Operator
git tag -d v3.1.0
git tag  v3.1.0
make
docker tag rancher/backup-restore-operator:v3.1.0 ${DOCKER_REPO}/${DOCKER_NAMESPACE}/rancher-backup-restore-operator:${DOCKER_TAG}
docker push ${DOCKER_REPO}/${DOCKER_NAMESPACE}/rancher-backup-restore-operator:${DOCKER_TAG}
```
