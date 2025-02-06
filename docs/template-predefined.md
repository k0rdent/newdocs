## Remove Templates shipped with k0rdent

If you need to limit the templates that exist in your k0rdent installation, follow the instructions below:

1. Get the list of `ProviderTemplate`, `ClusterTemplate` or `ServiceTemplate` objects shipped with k0rdent. For example,
for `ClusterTemplate` objects, run:

    ```bash
    kubectl get clustertemplates -n kcm-system -l helm.toolkit.fluxcd.io/name=kcm-templates
    ```
    ```console
    NAMESPACE    NAME                            VALID
    kcm-system   adopted-cluster-0-1-0           true
    kcm-system   aws-eks-0-1-0                   true
    kcm-system   aws-hosted-cp-0-1-0             true
    kcm-system   aws-standalone-cp-0-1-0         true
    kcm-system   azure-aks-0-1-0                 true
    kcm-system   azure-hosted-cp-0-1-0           true
    kcm-system   azure-standalone-cp-0-1-0       true
    kcm-system   openstack-standalone-cp-0-1-0   true
    kcm-system   vsphere-hosted-cp-0-1-0         true
    kcm-system   vsphere-standalone-cp-0-1-0     true
    ```

2. Remove the template from the list using `kubectl delete`, as in:

    ```bash
    kubectl delete clustertemplate -n kcm-system <template-name>
    ```