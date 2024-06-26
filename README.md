
# SFTPGo Helm Chart

This Helm chart deploys SFTPGo in a Kubernetes application using a Deployment and a Service.

## Chart Details

- **Chart Name:** SFTPGo
- **Version:** 0.1.0
- **App Version:** 1.0
- **Description:** A Helm chart for Kubernetes

## Prerequisites

- Kubernetes 1.16+
- Helm 3.0+

## Installing the Chart

To install the chart with the release name `sftpgo`, run the following command:

```bash
helm install sftpgo . -n 
```

## Uninstalling the Chart

To uninstall the `sftpgo` deployment, use the following command:

```bash
helm uninstall sftpgo -n <namespace>
```

This command removes all the Kubernetes components associated with the chart and deletes the release.

## Configuration

The following table lists the configurable parameters of the `SFTPGo` chart and their default values.

| Parameter            | Description                                      | Default       |
|----------------------|--------------------------------------------------|---------------|
| `replicaCount`       | Number of replicas for the Deployment            | `3`           |
| `image.repository`   | Image repository                                 | `SFTPGo`      |
| `image.tag`          | Image tag                                        | `1.0`         |
| `image.pullPolicy`   | Image pull policy                                | `IfNotPresent`|
| `service.type`       | Type of the service                              | `ClusterIP`   |
| `service.port`       | Service port                                     | `8080`        |

## Values

You can override the default values by specifying them in a `values.yaml` file or by using the `--set` flag during installation.
Keep in mind that to mount an already mounted volume is to have `accessModes: - ReadWriteMany` in each pvc.

### Example `values.yaml`

```yaml
replicaCount: 1

namespace: <namespace>

image:
  repository: drakkan/sftpgo
  tag: latest
  pullPolicy: IfNotPresent

service:
  type: ClusterIP

persistence:
  enabled: true
  pvcs:
    - name: Existing-PVC
      claimName: Existing-PVC
```
