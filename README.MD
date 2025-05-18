# Helm Chart Overview

This repository contains a Helm chart used for deploying Kubernetes applications efficiently and consistently.

## 📦 What is Helm?

[Helm](https://helm.sh/) is a package manager for Kubernetes that helps you define, install, and upgrade even the most complex Kubernetes applications using charts.

A **Helm chart** is a collection of files that describe a related set of Kubernetes resources.

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
