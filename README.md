# dify-agentic
dify-agentic
# AI Stack Kubernetes Deployment

## Overview
This repository provides a streamlined way to deploy an AI stack on Kubernetes using Kustomize. The stack includes essential services such as Dify API, plugins, a sandbox environment, SSRF protection, a web interface, worker services, and database components (PostgreSQL, Redis, Weaviate). Additionally, it supports GPU-powered models through the `gpustack` component.

## Features
- **Quick Deployment**: Easily deploy the AI stack with a single command.
- **Modular Design**: Developers can remove `gpustack` if using external model providers.
- **Extensibility**: Built with Kustomize, allowing easy modifications and extensions.
- **Support Open-Source**: Contributions and donations via Giter are encouraged!

## Deployment Instructions
### Prerequisites
Ensure you have the following installed:
- [Kubectl](https://kubernetes.io/docs/tasks/tools/)
- [Kustomize](https://kubectl.docs.kubernetes.io/installation/kustomize/)
- A running Kubernetes cluster

### Deploy the AI Stack
Run the following command to apply the configurations:
```sh
kubectl apply -k .
```

### Optional: Remove GPU Stack
If you are using an external model provider and do not need GPU resources, you can remove the `gpustack` component by editing `kustomization.yaml` and removing the following lines:
```yaml
# gpustack
- gpustack/deployments.yaml
- gpustack/services.yaml
```
Then, reapply the configuration:
```sh
kubectl apply -k .
```

## Components
The AI stack consists of the following services:
- **Dify API** (Core API service)
- **Dify Plugin** (Extends functionalities)
- **Dify Sandbox** (Testing and development environment)
- **Dify SSRF** (Security layer against SSRF attacks)
- **Dify Web** (Web frontend)
- **Dify Worker** (Background job processing)
- **PGAdmin & PostgreSQL** (Database management and storage)
- **Redis** (Caching and queueing)
- **Weaviate** (Vector database for AI indexing)
- **GPUStack** (Optional, for on-prem AI model serving)

## Dify web interface address:
http://dify-web.default.svc.cluster.local:3000, the **default init password** is `password`.

## PGAdmin web interface address:
http://pgadmin.default.svc.cluster.local:5050, the **default password** is `admin`.

## GPUStack web interface address:
http://gpustack.default.svc.cluster.local:3080

To retrieve the default admin password, run the following command:
```sh
kubectl exec -it gpustack -- cat /var/lib/gpustack/initial_admin_password
```

## Support & Contributions
We encourage developers to support this project via Giter donations. Contributions are also welcome—feel free to submit PRs or open issues for improvements!

Happy coding!


