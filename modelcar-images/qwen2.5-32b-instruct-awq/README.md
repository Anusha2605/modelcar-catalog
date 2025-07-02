# qwen2.5-7b-instruct

https://huggingface.co/qwen/qwen2.5-32b-instruct-awq

quay.io/redhat-ai-services/modelcar-catalog:qwen2.5-32b-instruct-awq

## Building Image

```
podman build modelcar-images/qwen2.5-7b-instruct \
    -t quay.io/redhat-ai-services/modelcar-catalog:qwen/qwen2.5-32b-instruct-awq  \
    --platform linux/amd64
```

## Deploying Model

This model can be deployed using vLLM on OpenShift AI using the following Helm Chart.

This configuration includes some specific configurations to deploy it on an NVIDIA A10G, which may require changes for your specific GPU.

```
helm repo add redhat-ai-services https://redhat-ai-services.github.io/helm-charts/
helm repo update redhat-ai-services
helm upgrade -i qwen2.5-32b-instruct-awq redhat-ai-services/vllm-kserve \
    --values modelcar-images/qwen2.5-32b-instruct-awq/values.yaml
```

For more information on the above Helm Chart, you can find the source code for that chart here:

https://github.com/redhat-ai-services/helm-charts/tree/main/charts/vllm-kserve
