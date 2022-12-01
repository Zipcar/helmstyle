# helmstyle
Deploy your helm charts with style


## How to use

helmstyle.yaml
```yaml
helmstyle:
  repositories:
  - name: bitnami
    url: https://charts.bitnami.com/bitnami
  releases:
  - name: rabbitmq
    chart: bitnami/rabbitmq
    values:
      nodeSelector:
        node.kubernetes.io/service: "true"
      resources:
        requests:
          memory: "500Mi"
        limits:
          memory: "2Gi"
```

`helmstyle apply -f helmstyle.yaml`


## Helmstyle vs Helmfile
* Helmfile currently requires you to give it a file path or directly with a helmfile in it.  With helmstyle you can just embed yaml into an existing document, or pass it via stdin, or direclty into the golang api without requiring file or directory access
* Helmfile calls out helm binary directly via go exec.  Helmstyle works standalone
* Helmstyle has a much smaller list of features and provides a simple go api




