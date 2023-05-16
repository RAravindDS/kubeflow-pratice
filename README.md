# kubeflow-pratice

**Kubeflow Pipeline Installation** 
```bash
# Install the kubeflow 
export PIPELINE_VERSION=1.8.5
kubectl apply -k "github.com/kubeflow/pipelines/manifests/kustomize/cluster-scoped-resources?ref=$PIPELINE_VERSION"
kubectl wait --for condition=established --timeout=60s crd/applications.app.k8s.io
kubectl apply -k "github.com/kubeflow/pipelines/manifests/kustomize/env/platform-agnostic-pns?ref=$PIPELINE_VERSION"

# Port forward the applicatoin after all the containers is "Running" 
kubectl port-forward -n kubeflow svc/ml-pipeline-ui 8080:80  #This will open a pipeline UI
```
[Documentation Link](https://www.kubeflow.org/docs/components/pipelines/v1/installation/localcluster-deployment/)