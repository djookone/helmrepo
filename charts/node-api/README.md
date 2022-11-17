# Node API

Node API chart to deploy new microservice

## Installing the chart

```
helm install --name my-release n9/node-api --namespace demo
```

> **Tip**: List all releases using `helm list`

## Uninstalling the Chart

To uninstall/delete the `my-release` deployment:

```console
$ helm del --purge my-release
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

## Configuration

If MongoDB, RabbitMQ and ElasticSearch URIs are changed,
a rolling-update is automatically triggered on the deployment.

The CPU limit is not set by default because of a CFS bug.
Google recommends to disable all CPU limits while waiting for the fix.
Kernel is patched in v4.18 but has not been fully tested yet.

| Parameter                                      | Description              | Default                                                    |
|------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------|
| `name` (REQUIRED)  | Deployment name | `name` |
| `global.pullSecrets`  | Array of pull secrets credentials for Docker | `[]` |
| `global.pullPolicy`  | Docker pull policy | `IfNotPresent` |
| `global.istio.enabled`  | Enable istio virtual service | `false` |
| `global.istio.retries`  | Istio number of retry for failed requests | `2` |
| `image.repository`  | Docker image repository | `repo` |
| `image.tag`  | Docker image tag | `latest` |
| `pod.replicas`  | Number of replicas | `1` |
| `pod.command`  | Pod command to override | `1` |
| `pod.minAvailable`  | Minimum number of replica available | `1` |
| `pod.annotations`  | Pod custom annotations | `{}` |
| `pod.configHash`  | Add custom configHash to trigger rolling-update  | "" |
| `pod.configMap.name`  | Config map name to mount | '' |
| `pod.configMap.path`  | Config map path to mount to | '' |
| `pod.env.secrets`  | Array of secrets with name and key to use | `[]` |
| `pod.env.values`  | Array of secrets with name and value to use | `[]` |
| `resources.limits.memory`  | Max memory usage | `180M` |
| `resources.limits.cpu`  | Max CPU usage | '' |
| `resources.requests.memory`  | Memory request | `180M` |
| `resources.requests.cpu`  | CPU request | `35m` |
| `healthCheck.path`  | Liveness probe path | `/ping` |
| `healthCheck.initialDelay`  | Liveness / Readiness probe initial delay | `3` |
| `healthCheck.periodSeconds`  | Liveness / Readiness probe interval | `10` |
| `healthCheck.timeoutSeconds`  | Liveness / Readiness probe interval | `1` |
| `service.type`  | Service type | `ClusterIP` |
| `service.port`  | Service port | `80` |
| `service.annotations`  | Service custom annotations | `{}` |
| `service.labels`  | Service custom labels | `{}` |
| `scale.enabled`  | Horizon pod autoscaler | `false` |
| `scale.min`  | Minimum pods | `1` |
| `scale.cpu`  | Start horizontal auto scaling at x% CPU request | `100` |
| `scale.memory`  | Start horizontal auto scaling at xM memory usage | `150M` |


