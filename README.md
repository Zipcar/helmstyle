# helmstyle
Deploy your helm charts with style

## How to use

helmstyle.yaml
```yaml
charts:
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

cat helmstyle.yaml | helmstyle apply 


## Helmstyle vs Helmfile
* Helmfile currently requires you to give it a file path or directly with a helmfile in it.   We would like to inline helmfile config with other yaml config, or just pass yaml directly to a go api to install
* Helmfile relies on a helm binary.   We would like to to just use helm and helmfile as go libraries for easier distribution

Helmstyle is intended to be a vastly simplified version of helmfile suitable for use as a go libary.  



