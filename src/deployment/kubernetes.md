# Deploy to Kubernetes

Notes:
- You must have at least 1 node labeled with scoretrak_worker=<your_internal_label> so scoretrak can correctly deploy workers.

## Prerequisites

Ensure you have the following prerequisites installed.

- [helm](https://helm.sh/docs/intro/install/#through-package-managers)

## Setup


In order to only deploy the workers that will score the services in the right place, it is recommended to label the k8s node using the "scoretrak_worker" label. For example, if I deployed 4 k8s nodes and only 2 nodes have access to the competitors internal network, you should add a scoretrak_worker label to those nodes.
```shell
# $ kubectl label nodes <your-node-name> <label>
$ kubectl label nodes node-3 scoretrak_worker=internal
$ kubectl label nodes node-4 scoretrak_worker=internal
...
```

## Steps

1. Setup your Kubernetes Cluster
    1. Your kubernetes cluster must have access to the service you wish to score

2. Install Scoretrak Helm Chart

Install scoretrak's helm chart repo from https://github.com/scoretrak/helm-charts

``` bash
$ helm repo add scoretrak https://scoretrak.github.io/helm-charts
```

3. Customize

Customize the default yaml file located in the [scoretrak helm chart](https://github.com/scoretrak/helm-charts/charts/scoretrak/values.yaml) to fit your environment.
Specifically the scoretrak.config section as that is what will be consumed by the server and worker.

4. Deploy

Install the helm chart

``` bash
helm install --timeout 1800 -f customized-values.yaml scoretrak/scoretrak
