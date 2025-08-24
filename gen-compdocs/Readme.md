# Overview

The `gen-compdocs` folder contains tools and scripts for generating Kubernetes component documentation. It automates extraction, formatting, and post-processing of component-level docs, helping maintainers and contributors keep documentation consistent and up to date.

# Prerequisites

- Go (>= 1.18) and `GO111MODULE=on`  
- `make` (for build automation)  
- Access to component source code or API definitions  
- `GOPATH` set if using legacy Go modules (when applicable)  
- Recommended: familiarity with Hugo and Kubernetes documentation conventions

# Usage / Process

1. **Build the generator**  
   - Use the Makefile or run Go directly from the `gen-compdocs` folder:  
     ```bash
     cd gen-compdocs
     make
     # or
     GO111MODULE=on go run main.go
     ```

2. **Generate component docs**  
   - Run the main entrypoint to generate docs for a specific component:  
     ```bash
     GO111MODULE=on go run main.go --component kube-apiserver
     ```
   - The generator orchestrates scripts in `comps/` and `generators/` to extract and format content.

3. **Post-process output**  
   - Run post-processing scripts in `generators/` for formatting, front matter, and cleanup.  
   - Inspect generated Markdown/Hugo files and verify front matter before publishing.

# Example cli usage

```bash
# Generate docs for the kubelet component
GO111MODULE=on go run main.go --component kubelet
````


# Whatsnext

* See `gen-apidocs` for API reference generation workflows.
* Review `content/en/docs/Reference/` for integration and publishing guidelines.
* Explore `genref/` for additional multi-format reference tooling.


