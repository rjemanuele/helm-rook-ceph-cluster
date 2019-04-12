# Rook Ceph Cluster Helm Chart

This helm chart can configure a Ceph cluster using and install of Rook.io previously set up
from https://rook.io/docs/rook/v0.9/helm-operator.html

## tl;dr

To create a basic filesystem backed cluster with replicated block devices usable by Kubernetes:

`$ helm install --namespace rook-ceph -n rook-ceph . --values=values.yaml`

To create a bluestore backed cluster utilizing `sdb` on each node in the cluster (in this case 
they are SSDs) with replicated block devices usable by Kubernetes:

`$ helm install --namespace rook-ceph-ssd -n rook-ceph-ssd . --values=values-production.yaml`

## Multiple Clusters

You can use this to create multiple clusters.  In fact, using both examples above will do just that.

*The important detail when creating multiple clusters, is that each cluster be in its own namespace and
use different paths for `dataDirHostPath`.*
