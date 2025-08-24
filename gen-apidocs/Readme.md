# Overview

The `gen-apidocs` folder contains tools and configuration files for generating Kubernetes API reference documentation. It automates extraction and formatting of API details from OpenAPI specifications, producing consistent, versioned reference pages for Kubernetes resources.

# Prerequisites

- Go (>= 1.18) and `GO111MODULE=on`
- Docker (optional, for containerized builds)
- Access to Kubernetes OpenAPI specs (swagger.json)
- `GOPATH` set if using legacy Go modules (when applicable)
- Recommended: familiarity with Hugo and Kubernetes documentation conventions

# Usage / Process

1. **Configure API versions**
    - Place OpenAPI specs (`swagger.json`) and config files in the appropriate `v1_xx/` subfolder under `config/`.

2. **Run the generator**
    - Build and run the generator from the `gen-apidocs` folder:
      ```bash
      cd gen-apidocs
      GO111MODULE=on go run main.go --version v1_33
      ```
    - Optionally run inside Docker for an isolated environment.

3. **Customize output**
    - Edit templates in `generators/` or config files in `config/` to adjust formatting, front matter, or sections.

4. **Review generated docs**
    - Inspect the generated Markdown/Hugo files in the output directory for completeness and correct front matter before publishing.

# Example cli usage

```bash
# Generate docs for a specific API version
GO111MODULE=on go run main.go --version v1_33
