# maps-tools-install

MaPS Tools is a Dockerized development environment that provides pre-configured CLI tools and manages credentials for AWS and related services (SSH and Kubernetes).

## Quick Install

```bash
bash <(curl -s https://raw.githubusercontent.com/spring-media/maps-tools-install/main/maps-tools)
```

## Documentation

For complete documentation, please visit:
- **[Installation & User Manual ⇨ as-infra.de/docs/platform/user-manual/Maps-tools](https://as-infra.de/docs/platform/user-manual/Maps-tools)**
- **[Tools Repository ⇨ github.com/spring-media/maps-tools](https://github.com/spring-media/maps-tools)**

## Quick Reference

### Usage

```bash
maps-tools - Docker-based tooling environment for AWS, Kubernetes, and Terraform

USAGE:
  maps-tools [OPTIONS]

COMMON OPTIONS:
  -h              Show this help message and exit
  --version       Print version number and exit

ENVIRONMENT OPTIONS:
  -e PROFILE      Set AWS profile/environment (e.g., mediasites-stage.dev)
                  Default: Uses $AWS_PROFILE if set

CONTAINER MODES:
  (default)       Run interactive container (removed after exit)
  -d              Create persistent daemon container in background
  -a              Attach to existing daemon container
  -E              Execute command in existing daemon container

CONFIGURATION:
  -v              Skip mounting local config directories (.aws, .ssh, .helm, .kube)
                  Use when you want an isolated container environment
  -s              Use session-specific kubeconfig instead of shared config
  -c              Backup and cleanup AWS and Kubernetes config files
                  Creates timestamped backups before removal

DOCKER OPTIONS:
  -i              Interactively select from locally available Docker images
  -o "ARGS"       Pass additional arguments to docker run/create
                  Can be used multiple times. Example: -o "-p 8080:8080"

FEATURES:
  -x              Enable Kubernetes dashboard (Octant) at http://0.0.0.0:7777/
  -u [VERSION]    Check for updates and optionally install
                  Optional: -u testing (for testing release channel)
```

### Common Examples

```bash
# Run standard interactive container
maps-tools

# Start with specific AWS profile
maps-tools -e mediasites-stage.dev

# Create background daemon container
maps-tools -d

# Attach to existing daemon
maps-tools -a

# Execute command in daemon container
maps-tools -E "kubectl get pods"

# Start with Kubernetes dashboard
maps-tools -x

# Check for updates
maps-tools -u
```

## Release Channels

- **`latest`** - Production stable release
- **`testing`** - Development build from master branch
- **`feature-<PR-number>`** - Pull request testing builds

## Repository Structure

This repository contains the installation scripts:
- `maps-tools` - Stable release installer
- `maps-tools-testing` - Testing release installer

The Docker image and tools are maintained in the [maps-tools repository](https://github.com/spring-media/maps-tools).
