# Overview

The `gen-kubectldocs` folder contains tools and scripts for generating reference documentation for the `kubectl` command-line tool. It automates extraction, formatting, and organization of command docs across Kubernetes versions, helping ensure consistent and accurate published documentation.

# Prerequisites

- Go (>= 1.18) and `GO111MODULE=on`  
- Docker (optional, for containerized builds)  
- Access to `kubectl` source or command definitions  
- `GOPATH` set if using legacy Go modules (when applicable)  
- Recommended: familiarity with Hugo and Kubernetes documentation conventions

# Usage / Process

1. **Configure versions**  
   - Place version-specific files (for example, `toc.yaml` and static markdown includes) in the appropriate `v1_xx/` subfolder under `generators/`.  

2. **Run the generator**  
   - Build and run the generator from the `gen-kubectldocs` folder:  
     ```bash
     cd gen-kubectldocs
     GO111MODULE=on go run main.go --version v1_26
     ```
   - Optionally run inside Docker for an isolated environment.

3. **Customize output**  
   - Edit templates and config files in `generators/` to adjust formatting, front matter, and content structure.

4. **Review generated docs**  
   - Inspect the generated Markdown/Hugo files in the output directory and verify front matter and TOC before publishing.

# Example cli usage

```bash
# Generate kubectl docs for a specific version
GO111MODULE=on go run main.go --version v1_26
````

# Whatsnext

* See `gen-apidocs` for API reference generation workflows.
* See `gen-compdocs` for component documentation generation.
* Review `content/en/docs/Reference/` for integration and publishing guidelines.
* Explore `genref/` for additional multi-format reference tooling.

