# Helm Chart Overview

This repository contains a Helm chart used for deploying Kubernetes applications efficiently and consistently.

## 📦 What is Helm?

[Helm](https://helm.sh/) is a package manager for Kubernetes that helps you define, install, and upgrade even the most complex Kubernetes applications using charts.

A **Helm chart** is a collection of files that describe a related set of Kubernetes resources.

**Helm** is a package manager for Kubernetes — similar to how `dnf` or `yum` works in RHEL/Linux.

Helm serves two primary purposes:

1. **Package Management for Kubernetes**
   - Helm allows you to install, upgrade, and uninstall Kubernetes applications packaged as **Helm charts**.
   - Charts bundle all the Kubernetes resources needed for deploying an application or service.

2. **Templatizing Kubernetes Manifests**
   - Helm enables you to write manifest files using **Go templates**, which makes them reusable and configurable.
   - You can use variables, loops, conditionals, and default values to dynamically generate YAML files based on input values.

By using Helm, teams can manage complex Kubernetes deployments with version control, rollbacks, and configurable parameters.

---

## 📁 Chart Structure

mychart/

├── Chart.yaml # Metadata about the chart (name, version, etc.)

├── values.yaml # Default configuration values

├── templates/ # Kubernetes manifest templates (Deployment, Service, etc.)

├── charts/ # (Optional) Directory for chart dependencies

└── README.md # Chart overview and usage


---

## 📜 Files Description

### `Chart.yaml`
- Contains chart metadata like name, version, description, and dependencies.

### `values.yaml`
- Provides default configuration values.
- These can be overridden during installation using `--values` or `--set`.

### `templates/`
- Contains Go template-based Kubernetes YAML files (e.g., `deployment.yaml`, `service.yaml`, `ingress.yaml`).
- These templates are rendered using values from `values.yaml`.

### `charts/`
- (Optional) Stores chart dependencies (subcharts).
- Automatically populated when you run `helm dependency update`.

---

## 🚀 Installing the Chart

```bash
helm install <release-name> ./mychart
```

To override default values:

```sh
helm install <release-name> ./mychart -f custom-values.yaml
```

Or with inline overrides:
```sh
helm upgrade <release-name> ./mychart
```

## 🧰 Useful Helm Commands

```
helm lint ./mychart                     # Validate the chart
helm template ./mychart                # Render templates locally
helm show values ./mychart             # View default values
helm uninstall <release-name>          # Delete a release
```

## 📦 Helm Repositories

A **Helm repository** is a place where **Helm charts** are stored and shared.  
It functions similarly to package repositories in Linux, such as APT or YUM Repos.

Repositories make it easy to organize, store, and distribute Helm charts.  
They also support **versioning**, allowing you to install specific versions of a chart as needed.

### 🔧 Common Helm Repository Commands

- **Add a Repository:**
```bash
helm repo add bitnami https://charts.bitnami.com/bitnami
```
- **List Added Repositories:**
```
helm repo list
```
- **Update Repositories:**
```
helm repo update
```

## 🚀 Helm Releases

A **Helm release** is a deployed instance of a Helm chart in your Kubernetes cluster.  
Think of it as a running version of your application managed by Helm.

Releases allow you to install, upgrade, roll back, and uninstall applications easily.  
You can also manage multiple instances of the same chart with different configurations.

### 🔧 Common Helm Release Commands

- **Create a Release:**
```bash
helm install myapp ./myapp
```



- **List All Releases:**

```
helm list
```

- **Upgrade a Release:**

```
helm upgrade myapp ./myapp
```

- **Roll Back to a Previous Version:**

```
helm rollback myapp 1
```

- **Delete a Release:**

```
helm uninstall myapp
```

### Helm releases are helpful for:

* Tracking deployed versions

* Performing rollbacks in case of issues

* Managing multiple environments (e.g., myapp-dev, myapp-prod)