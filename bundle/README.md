# OpenShift Packaging Docs
Here's a current state of the OpenShift packaging of our K8s operator.

- Packaging has been manually validated and can be deployed from Quay.io (see build-registry-quay for an example that uses my Quay account) to an arbitrary namespace in an OpenShift 4.5 cluster
- Package certification is currently blocked by an unknown issue with the OpenShift certification CI, waiting for feedback from Red Hat (9.18.20 2 pm)
- Current package does not yet incorporate Chris's changes to run the crdb container as a non-root user, so the SCC in the clusterserviceversion for `default` is being set to `anyuid`, which will change to `nonroot` in the near future
- Current package leverages Red Hat specific CRDB container images

##Packaging Docs
Certified Operator Guide -https://redhat-connect.gitbook.io/certified-operator-guide/appendix/bundle-maintenance-after-migration
Operator SDK Guide - https://docs.openshift.com/container-platform/4.5/operators/operator_sdk/osdk-getting-started.html
Example Operator - https://github.com/redhat-marketplace/redhat-marketplace-operator

##TODO
- update generated CRD to remove header block and remove -image from required
- update generated ClusterServiceVersion to match example 
- auto-build and deploy packaging to Red Hat container registry
- complete outstanding packaging items
- rbac for cockroach-operator-role needs to be trimmed to least required permissions
