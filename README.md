# Camel Helmet Demo

This repository contains a demo application showcasing the integration of Apache Camel with Kubernetes using Helm charts and the [Helmet](https://artifacthub.io/packages/helm/companyinfo/helmet) library.

## Features

- Apache Camel routes for message processing.
- Helm chart for Kubernetes deployment.
- Configurable and scalable architecture.

## Prerequisites

- Kubernetes cluster
- Helm 3.x
- Apache Camel knowledge (optional)

## Installation

1. Clone the repository:
    ```bash
    git clone https://github.com/rmortale/camel-helmet-demo
    cd camel-helmet-demo
    ```
2. Install Jbang and Apache Camel app following the [docs](https://camel.apache.org/manual/camel-jbang.html).

3. To test the route localy execute:
    ```bash
    camel run --dev routes/demo.camel.yaml
    ```

4. Deploy the application using Helm:
    ```bash
    helm install camel-helmet-demo . -f devt-values.yaml
    ```
    Or apply the ApplicationSet under argocd in argocd namespace with :
    ```bash
    kubectl apply -f argocd/application-set.yaml
    ```


5. Verify the deployment:
    ```bash
    kubectl get pod
    ```
6. Uninstall the deployment:
    ```bash
    helm delete helmet-demo
    ```
    Or if you applied the ApplicationSet with in argocd namespace:
    ```bash
    kubectl delete -f argocd/application-set.yaml
    ```
## Usage

- Modify the Camel routes in the `routes` directory to suit your needs.
- Add more values files for other kubernetes environments if needed.

## Contributing

Contributions are welcome! Please open an issue or submit a pull request.



