# yaml-jq

```bash
docker build -t giantswarm/yaml-jq .
```

```bash
cat example/kube-apiserver.yaml \
  | docker run -i giantswarm/yaml-jq '
    .spec.containers[0].volumeMounts
      |= .+ [{"mountPath": "/var/log/kubernetes", "name": "audit"}] |
    .spec.volumes
      |= .+ [{"hostPath": {"path": "/var/log/kubernetes"}, "name": "audit"}]'
```
