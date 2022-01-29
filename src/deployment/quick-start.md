# Quick Start

ScoreTrak currently supports deploying via docker, docker swarm and kubernetes. You can find the docker container stored in the github container registry located in the [scoretrak org page](https://github.com/orgs/ScoreTrak/packages).

## Usage

You can deploy on many platforms and each can found below.

1. [Kubernetes](#Deploy to Kubernetes)


## Deploy to Kubernetes

Notes:
- You must have at least 1 node labeled with scoretrak_worker=<your_internal_label> so scoretrak can correctly deploy workers.

### Prerequisties

Ensure you have the following prerequisties installed.

- [helm](https://helm.sh/docs/intro/install/#through-package-managers)

### Steps

1. Install Scoretrak Helm Chart

Install scoretrak's helm chart repo from https://github.com/scoretrak/helm-charts

``` bash
$ helm repo add scoretrak https://scoretrak.github.io/helm-charts
```

2. Customize

Customize the default yaml file located in the [scoretrak helm chart](https://github.com/scoretrak/helm-charts/charts/scoretrak/values.yaml) to fit your environment.

3. Deploy

Install the helm chart

``` bash
helm install --timeout 1800 -f customized-values.yaml scoretrak/scoretrak
```