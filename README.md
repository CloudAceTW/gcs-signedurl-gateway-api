# GCS Signed URL Gateway API

This project provides a Kubernetes Gateway API implementation for generating signed URLs for Google Cloud Storage (GCS) objects. It leverages a backend service written in Go ([https://github.com/CloudAceTW/go-gcs-signedurl](https://github.com/CloudAceTW/go-gcs-signedurl)) and a front-end application built with Vue ([https://github.com/CloudAceTW/vue-gcs-signedurl](https://github.com/CloudAceTW/vue-gcs-signedurl)).


## Before Use

Due to [Cross-Namespace routing](https://gateway-api.sigs.k8s.io/guides/multiple-ns/), you need to configure your Kubernetes namespace with the label `shared-gateway-access=true`.

For example:
```bash
kubectl label namespace <YOUR_NS> shared-gateway-access=true
```

## Deployment on GKE
1. Prepare the Helm Chart:
    - Copy the example configuration file:
    ```bash
    cp chart/values.yaml.example chart/values.yaml
    ```

    - Edit the chart/values.yaml file to configure the gateway:
    ```bash
    vim chart/values.yaml
    ```
2. Install with Helm:
    - Install the gateway using Helm:
    ```bash
    helm install signurl-gw ./chart -n <NAMESPACE>
    ```
