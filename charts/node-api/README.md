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
| `image.digest`  | Docker image digest | `null` |
| `serviceAccount.create`  | Create service account for deployment | `false` |
| `serviceAccount.name`  | Name of the service account | `false` |
| `pod.replicas`  | Number of replicas | `1` |
| `pod.command`  | Pod command to override | `1` |
| `pod.workingDir`  | Pod workingDir | "" |
| `pod.minAvailable`  | Minimum number of replica available | `1` |
| `pod.annotations`  | Pod custom annotations | `{}` |
| `pod.configHash`  | Add custom configHash to trigger rolling-update  | "" |
| `pod.configMap.name`  | Config map name to mount | '' |
| `pod.configMap.path`  | Config map path to mount to | '' |
| `pod.extraConfigmapMounts`  | extra configmap to mount | `[]` |
| `pod.extraSecretMounts`  | extra secrets to mount | `[]` |
| `pod.env.secrets`  | Array of secrets with name and key to use | `[]` |
| `pod.env.values`  | Array of secrets with name and value to use | `[]` |
| `resources.limits.memory`  | Max memory usage | `180M` |
| `resources.limits.cpu`  | Max CPU usage | '' |
| `resources.requests.memory`  | Memory request | `180M` |
| `resources.requests.cpu`  | CPU request | `35m` |
| `healthCheck.port`  | Liveness probe port | `{{ service.targetPort }}` |
| `healthCheck.path`  | Liveness probe path | `/ping` |
| `healthCheck.initialDelaySeconds`  | Liveness / Readiness probe initial delay | `3` |
| `healthCheck.periodSeconds`  | Liveness / Readiness probe interval | `10` |
| `healthCheck.timeoutSeconds`  | Liveness / Readiness timeout | `1` |
| `healthCheck.failureThreshold`  | Liveness / Readiness failure threshold | `3` |
| `service.type`  | Service type | `ClusterIP` |
| `service.port`  | Service port | `80` |
| `service.targetPort`  | Service port | `{{ service.port }}` |
| `service.annotations`  | Service custom annotations | `{}` |
| `service.labels`  | Service custom labels | `{}` |
| `scale.enabled`  | Horizon pod autoscaler | `false` |
| `scale.min`  | Minimum pods | `1` |
| `scale.cpu`  | Start horizontal auto scaling at x% CPU request | `100` |
| `scale.memory`  | Start horizontal auto scaling at x% memory request | `80` |
| `metrics.port`  | Metrics port number to add to the service | '' |
| `metrics.targetPort`  | If the pod metrics port is different than the service metrics port | `metric.port` |
| `metrics.label`  | Service and deployment value for metrics label | `prometheus` |
| `metrics.enabled`  | Enable metrics for prometheus | `false` |
| `metrics.serviceMonitor.enabled`  | Enable service monitor for prometheus | `false` |
| `metrics.serviceMonitor.interval`  | Interval used by prometheus-operator to scrap metrics | `15s` |
| `metrics.serviceMonitor.app.enabled`  | Enable service monitor of application metrics for prometheus | `false` |
| `metrics.serviceMonitor.envoy.enabled`  | Enable envoy metrics for prometheus | `false` |
| `metrics.serviceMonitor.envoy.port`  | Envoy metrics service monitor port number to add to service definition | `9102` |
| `metrics.serviceMonitor.envoy.targetPort`  | If envoy metrics port number is different than the service port | `9102` |
| `nodeSelector`  | pod scheduling node selector | `{}` |
| `affinity`  | pod scheduling affinity | `{}` |
| `tolerations`  | pod scheduling tolerations | `[]` |


