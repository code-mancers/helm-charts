# Dockup

[Dockup](https://dockup.app/) creates disposable staging environments on the fly
as many as you want!


## Installing the Chart

To install the chart with the release name `my-release`:

```bash
$ helm repo add c9s https://helm-charts.c9s.tech
$ helm repo update

$ helm install c9s/dockup --name my-dockup
```

## Uninstalling the Chart

To uninstall/delete the `my-release` deployment:

```bash
$ helm delete --purge my-release
```

The command removes all the Kubernetes components associated with the chart and
deletes the release.

## Configuration

The following table lists the configurable parameters of the Traefik chart and
their default values.

| Parameter                              | Description                                                               | Default                                           |
| -------------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------- |
| `ingress.hosts[0]`                     | Url where dockup UI has to be accessible                                  | `ui.dockup.yourdomain.com`                        |
| `baseDomain`                           | Base domain used for all dockup deployments                               | `dockup.yourdomain.com`                           |
| `maxConcurrentDeployments`             | Maximum deploys allowed                                                   | 10                                                |
| `maxConcurrentBuilds`                  | Maximum builds allowed at a given time                                    | 10                                                |
| `slackWebhookUrl`                      | Url where dockup will inform slack notifications                          | `test`                                            |
| `hibernateAllAt`                       | Time in hh:mm:ss format to hibrenate all deploys. Eg: "14:30:00"          | unset                                             |
| `wakeUpAllAt`                          | Time in hh:mm:ss format to wake-up all deploys. Eg: "14:30:00"            | unset                                             |
| `dockupSubdomainPool`                  | Name for url subdomains                                                   | unset                                             |
| `dockupCustomerName`                   | Customer name for metrics                                                 | codemancers                                       |
| `dockupMetricsEndpoint`                | Endpoint to report metrics                                                | https://subdomainfirebaseio.com (dummy)           |


Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`. For example:

```bash
$ helm install --name my-release \
  --set baseDomain.enabled=dockup.acme.com c9s/dockup
```
Alternatively, a YAML file that specifies the values for the parameters can
be provided while installing the chart. For example:

```bash
$ helm install --name my-release --values values.yaml c9s/dockup
```