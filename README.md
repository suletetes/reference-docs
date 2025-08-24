# {{% heading "overview" %}}

The `reference-docs` repository provides automated tools and workflows for generating Kubernetes API, CRD, component, and command reference documentation. Its purpose is to ensure that reference documentation remains accurate, consistent, and up to date across Kubernetes releases. Contributors use this repo to build, update, and publish docs for core APIs, controllers, CLI tools, and custom resources.

# {{% heading "prerequisites" %}}

Before using any tools in this repository, ensure you have:

- Go (>= 1.18)
- Python (for some scripts)
- Make (for build automation)
- Docker (optional, for containerized builds)
- Access to Kubernetes source code and OpenAPI specs
- Familiarity with Hugo and Kubernetes documentation standards
- Environment variables (examples used by tools):
  - `K8S_ROOT`
  - `K8S_WEBROOT`
  - `K8S_RELEASE`
  - `GO111MODULE=on` (if applicable)

# {{% heading "documentation generation workflow" %}}

1. **Configure source files:** Place OpenAPI specs, CRD definitions, or config files in the appropriate versioned subfolders.
2. **Set environment variables:** Export the environment variables required by the tooling (for example `K8S_ROOT`, `K8S_WEBROOT`, `K8S_RELEASE`).
3. **Run generators:** Use the provided Go binaries, scripts, or Makefile targets in each subfolder to generate documentation. Tools typically support flags for version, format, and output location.
4. **Review and integrate output:** Inspect generated Markdown/Hugo files for completeness and formatting, then copy or commit them into the website content directory (for example `content/en/docs/Reference/`).
5. **Customize templates (optional):** Edit templates in each tool's folder to adjust formatting or front matter as needed.

# {{% heading "folder breakdown" %}}

- [`gen-apidocs/`](./gen-apidocs/README.md): Generates API reference documentation from OpenAPI specs.
- [`gen-compdocs/`](./gen-compdocs/README.md): Produces component-level documentation for Kubernetes controllers and services.
- [`gen-kubectldocs/`](./gen-kubectldocs/README.md): Automates generation of `kubectl` command reference docs across versions.
- [`gen-resourcesdocs/`](./gen-resourcesdocs/README.md): Builds resource-level documentation for core and custom resources.
- [`genref/`](./genref/README.md): Generates reference docs for APIs and components in multiple formats.
- [`cmd/` and `scripts/`]: CLI entrypoints and helper scripts used across generators (see each README for details).

# {{% heading "benefits" %}}

- Ensures consistent, high-quality reference docs for Kubernetes.
- Reduces manual effort for maintainers and contributors.
- Supports multiple versions and output formats.
- Facilitates onboarding and review for new contributors.

# {{% heading "whatsnext" %}}

- Review the documentation pages for each major folder:
  - [gen-apidocs](./gen-apidocs/README.md)
  - [gen-compdocs](./gen-compdocs/README.md)
  - [gen-kubectldocs](./gen-kubectldocs/README.md)
  - [gen-resourcesdocs](./gen-resourcesdocs/README.md)
  - [genref](./genref/README.md)
- Consult the SIG Docs contribution guide for best practices and publishing workflows.
- Explore integration points under `content/en/docs/Reference/` for publishing generated docs.
