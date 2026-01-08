# Travelo CI/CD Templates

Reusable GitHub Actions workflows for Travelo project.

## Available Workflows

### 1. `docker-build.yml`
Builds Docker images with optional caching.

**Inputs:**
- `image-name`: Docker image name (required)
- `artifact-name`: Artifact name for upload (required)
- `enable-cache`: Enable Docker layer caching (default: false)
- `cache-key-file`: File to hash for cache key (default: package-lock.json)

### 2. `docker-push.yml`
Pushes Docker images to Docker Hub.

**Inputs:**
- `image-name`: Docker image name (required)
- `artifact-name`: Artifact name to download (required)
- `support-version-tags`: Support version tags (default: false)

**Secrets:**
- `dockerhub-username`: Docker Hub username
- `dockerhub-token`: Docker Hub token

### 3. `gitops-deploy.yml`
Updates infrastructure repo with new image tags.

**Inputs:**
- `image-name`: Docker image name (required)
- `yaml-file`: YAML file to update (required)
- `infra-repo`: Infrastructure repository (required)
- `support-version-tags`: Support version tags (default: false)

**Secrets:**
- `infra-token`: GitHub token for infra repo

## Usage Example

```yaml
jobs:
  build:
    uses: Alae-J/travelo-ci-templates/.github/workflows/docker-build.yml@main
    with:
      image-name: alaej/travelo-frontend
      artifact-name: frontend-image
      enable-cache: true
```
