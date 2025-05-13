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
4. When finished with the development copy the route body into the `devt-values.yaml` file into the configMap.

    ```bash
    ...
    configMap:
      mounted: true
      mountPath: /integrations
      data:
        demo.camel.yaml: |
          - route:
            from:
              uri: timer:yaml
              parameters:
                period: "1000"
              steps:
                - setBody:
                    simple: Hello Camel from ${routeId}
                - log: ${body}
    ```

2. Deploy the application using Helm:
    ```bash
    helm install camel-helmet-demo ./helm-chart
    ```

3. Verify the deployment:
    ```bash
    kubectl get pods
    ```

## Usage

- Modify the Camel routes in the `devt-values.yaml` file to suit your needs.
- Add more values files for other kubernetes environment if needed.

## Contributing

Contributions are welcome! Please open an issue or submit a pull request.



