# k6 load test

This repository contains a simple Helm chart to deploy an NGINX application, along with the resources required to run [k6](https://k6.io/) load testing. The chart and configuration files are designed to work in a Kubernetes environment with tools like ArgoCD, Kargo, Vault, and observability stacks.

---

## Repository Structure
```
.
├── charts/                  # Helm chart to deploy NGINX
└── resources/
    ├── argocd-dev.yaml      # ArgoCD application for dev namespace
    ├── argocd-prod.yaml     # ArgoCD application for prod namespace
    └── kargo.yaml           # Kargo project setup with stages and analysis
```
---

## Pre-requisites

Make sure the following tools are installed and running in your Kubernetes cluster:

- [Minikube](https://minikube.sigs.k8s.io/)
- [Helm](https://helm.sh/)
- [Vault](https://www.vaultproject.io/)
- [k6-operator](https://github.com/grafana/k6-operator)
- [ArgoCD](https://argo-cd.readthedocs.io/)
- [Kargo](https://kargo.akuity.io/)
- [OpenTelemetry](https://opentelemetry.io/)
- [Prometheus](https://prometheus.io/)
- [Grafana](https://grafana.com/)

Use the scripts from the following repo to install the prerequisites:
👉 [https://github.com/vibakar/k8s-tool-installer](https://github.com/vibakar/k8s-tool-installer)

---

## Setup Instructions

1. **Clone this repository**

   ```bash
   git clone https://github.com/your-username/your-repo-name.git
   cd your-repo-name

2. **Update kargo.yaml**

   Open resources/kargo.yaml and update the placeholder values:

   * Replace the placeholders for Docker and GitHub credentials with your actual values.

   * Set the correct Keycloak token URL where indicated.

   These are marked with `<<REPLACED_ME>>` in the file and must be updated before applying the configuration.

3. **Set Vault Secrets**

   Save your Keycloak client-id and client-secret credentials in Vault at the following path:

    `v1/kv2/data/react-demo-svc-client`

4. **Apply Resources**

    Once all tools are installed and configured

    run `kubectl apply -f resources/`
