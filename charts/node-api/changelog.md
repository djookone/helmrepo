# 1.16.0

**Breaking changes**:

- Rename `healthCheck.initialDelay` to `healchCheck.initialDelaySeconds`

Other changes:

- Add `healthcheck.failureThreshold` override option

# 1.15.1

- Fix pod container port

# 1.15.0

- Add `healthCheck.port` var to specify port healthchecks

# 1.14.1

- Fix resources block indentation

# 1.14.0

- Create servicemonitor only when metrics.serviceMonitor.enabled == true
- Fix remaining blank lines
- Use trim with toYaml for better formatting
- Fix service annotations indentation
- Update general indentation
- Fix envoy metrics targetPort

# 1.13.1

- Fix custom metrics indentation

# 1.13.0

- Add custom metrics support

# 1.12.0

- Add service monitor for envoy

# 1.11.1

- Fix service monitor label

# 1.11.0

- Add support for pod `nodeSelector`, `affinity` and `tolerations`

# 1.10.4

- Fix typo Vals instead of Values

# 1.10.3

- Fix volumeMounts indentation for .Values.pod.configMap

# 1.10.2

- Fix configmap indentation

# 1.10.1

- Fix service monitor namespace

# 1.10.0

- Add possibility to use image digest for deployment

# 1.9.0

- Update scale memory metric from memory value to memory percentage

# 1.8.0

- Add support of serviceMonitor for prometheus-operator
- Add extraConfigmapMounts to range over provided configmap list
- Add extraSecretMounts to range over provided secret list

# 1.7.0

- Add label metrics support

# 1.6.0

- Add metrics support

# 1.5.1

- Fix default serviceAccount name

# 1.5.0

- Add serviceAccount support

# 1.4.1

- Fix secret when value is a number and not a string

# 1.4.0

- Add `workingDir` pod option

# 1.3.0

- Add optionnal `configMap.key` to volumeMounts

# 1.2.0

- ConfigHash has been moved to global values

# 1.1.1

- Fix envs values key name

# 1.1.0

- Add support custom raw env variables with `pod.values`
- Add support for command with `pod.command`
