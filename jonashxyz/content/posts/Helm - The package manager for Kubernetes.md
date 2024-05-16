---
title: 'Helm - The package manager for Kubernetes'
date: 2024-05-16
tags:
- Article
- Kubernetes
- DevOps
- Helm
draft: false
---

#Kubernetes #Helm #DevOps 
## Helm
Helm is the best way to find, share, and use software built for [Kubernetes](https://kubernetes.io). It helps you manage Kubernetes applications and helps you define, install, and upgrade even the most complex Kubernetes application.

Helm is a graduated project in the [CNCF](https://cncf.io) and is maintained by the [Helm community](https://github.com/helm/community).
## What is a helm chart?
a Helm chart is a powerful tool that simplifies the deployment, management, and sharing of applications on Kubernetes by packaging all necessary resources and configurations into a single, reusable unit.

In other words, a Helm chart is a package that contains all the necessary information and resources to deploy an application or service onto a Kubernetes cluster. It includes a collection of files that describe a related set of Kubernetes resources.

Charts are easy to create, version, share, and publish — so start using Helm and stop the copy-and-paste.
## How to install helm
https://helm.sh/docs/intro/install/

### Example Structure of a Helm Chart
```
mychart/
  Chart.yaml        # Chart metadata
  values.yaml       # Default configuration values
  charts/           # Dependency charts (optional)
  templates/        # Templates for Kubernetes resources
    deployment.yaml
    service.yaml
    ...
  README.md         # Documentation (optional)
```

### Components and functionality of a Helm chart:
1. **Chart.yaml**: This file contains metadata about the chart, including the name, version, description, and any dependencies on other charts.

2. **Values.yaml**: This file defines the default configuration values for the chart. Users can override these values when they install or upgrade a chart to customize the deployment.

3. **Templates**: This directory contains a set of templates that generate Kubernetes manifest files. The templates use [Go](https://go.dev/) templating syntax and can include variables that are defined in `Values.yaml` or provided by the user at installation time.

4. **Charts**: This directory (optional) can contain dependencies, which are other charts that this chart depends on.

5. **Files**: Additional files can be included in the chart for reference, such as `README.md` or any other documentation.

### How Helm Charts Work
- **Packaging**: Helm charts are packaged into `.tgz` (tarball) files, which can be distributed and shared.
- **Installation**: When you install a chart using the `helm install` command, Helm takes the templates, substitutes any values, and generates Kubernetes manifests that are then applied to the Kubernetes cluster.
- **Customization**: Users can provide their own configuration values via the `--values` or `--set` flags to customize the deployment without modifying the chart's source code.
- **Versioning**: Charts can be versioned, allowing for consistent deployments and the ability to roll back to previous versions if necessary.

### What are the benefits of using Helm Charts?
- **Reusability**: Helm charts encapsulate Kubernetes resources into reusable packages, making it easy to share and reuse configurations across different environments.
- **Simplified Management**: Helm abstracts the complexity of Kubernetes configurations, making it easier to manage and deploy applications.
- **Dependency Management**: Helm manages dependencies between different charts, ensuring that all required services are deployed in the correct order.
- **Version Control**: Helm charts support versioning, which helps in tracking changes and rolling back to previous versions when needed.
- **Customization**: The ability to override default values allows users to customize deployments without altering the original chart.

### Common Helm commands
1. **`helm repo add <repo-name> <repo-url>`**
   - Adds a Helm chart repository to your local Helm client.
   - **Example**: `helm repo add stable https://charts.helm.sh/stable`

2. **`helm repo update`**
   - Updates the local cache of the Helm chart repositories.
   - **Example**: `helm repo update`

3. **`helm search repo <keyword>`**
   - Searches for charts in the added repositories that match the given keyword.
   - **Example**: `helm search repo nginx`

4. **`helm install <release-name> <chart> [flags]`**
   - Installs a Helm chart to create a new release.
   - **Example**: `helm install my-nginx stable/nginx-ingress`

5. **`helm upgrade <release-name> <chart> [flags]`**
   - Upgrades an existing release to a new version of the chart.
   - **Example**: `helm upgrade my-nginx stable/nginx-ingress`

6. **`helm uninstall <release-name> [flags]`**
   - Uninstalls a release from the Kubernetes cluster.
   - **Example**: `helm uninstall my-nginx`

7. **`helm list [flags]`**
   - Lists all releases in the current namespace.
   - **Example**: `helm list`

8. **`helm status <release-name>`**
   - Displays the status of the specified release.
   - **Example**: `helm status my-nginx`

9. **`helm rollback <release-name> <revision>`**
   - Rolls back a release to a specific revision.
   - **Example**: `helm rollback my-nginx 1`

10. **`helm template <chart> [flags]`**
    - Generates Kubernetes manifest files from a Helm chart without actually installing the chart.
    - **Example**: `helm template stable/nginx-ingress`

11. **`helm show values <chart>`**
    - Displays the default values for a Helm chart.
    - **Example**: `helm show values stable/nginx-ingress`

12. **`helm get all <release-name>`**
    - Retrieves all information about a specific release, including values, hooks, and manifest files.
    - **Example**: `helm get all my-nginx`

13. **`helm package <chart-path> [flags]`**
    - Packages a Helm chart directory into a `.tgz` (tarball) file.
    - **Example**: `helm package ./mychart`

14. **`helm lint <chart>`**
    - Runs a series of tests to ensure that a chart follows best practices.
    - **Example**: `helm lint ./mychart`

15. **`helm test <release-name> [flags]`**
    - Runs tests for a release to validate its deployment.
    - **Example**: `helm test my-nginx`

16. **`helm dependency update [flags]`**
    - Updates the dependencies for a chart based on the `Chart.yaml` file.
    - **Example**: `helm dependency update ./mychart`

17. **`helm pull <chart> [flags]`**
    - Downloads a chart from a repository and (optionally) decompresses it.
    - **Example**: `helm pull stable/nginx-ingress`

18. **`helm repo list`**
    - Lists all the repositories that have been added.
    - **Example**: `helm repo list`

These commands cover the most common tasks you'll perform with Helm, from managing repositories and searching for charts to installing, upgrading, and maintaining releases.
## Links :

202405161033

https://helm.sh/
