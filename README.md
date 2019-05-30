# EFK Helm Chart Based on Elastic-Stack

This chart installs an elasticsearch cluster with kibana and fluentd by default. Based on stable/elastic-stack.

## Prerequisites Details

* Kubernetes 1.8+
* PV dynamic provisioning support on the underlying infrastructure

## Chart Details
This chart will do the following:

* Implemented a dynamically scalable elasticsearch cluster using Kubernetes StatefulSets/Deployments
* Multi-role deployment: master, client (coordinating) and data nodes
* Statefulset Supports scaling down without degrading the cluster

## Installing the Chart

To install the chart with the release name `my-release`:

```bash
$ helm install --name my-release . 
```
NOTE: You need to update values.yaml to reflect your release name. Replace RELEASENAME with the
chosen release name.

## Deleting the Charts

Delete the Helm deployment as normal

```
$ helm delete my-release
```

Deletion of the StatefulSet doesn't cascade to deleting associated PVCs. To delete them:

```
$ kubectl delete pvc -l release=my-release,component=data
```
