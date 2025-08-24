# Overview

The `genref` folder provides a reference documentation generator that parses Go types (using `k8s.io/gengo`) and produces API and component reference documentation in HTML or Markdown. It supports multiple output formats and versions, enabling maintainers to produce consistent, up-to-date reference docs for various Kubernetes objects and configurations.

# Prerequisites

- Go (>= 1.18) and `GO111MODULE=on`  
- `make` (for build automation)  
- Access to Kubernetes API/type definitions and configs  
- `GOPATH` set if using legacy Go modules (when applicable)  
- Recommended: familiarity with Hugo and Kubernetes documentation conventions

# Process

1. **Build the generator**  
   - From the `genref` folder, build the binary using `make` or run Go directly:  
     ```bash
     cd genref
     make
     # or
     GO111MODULE=on go run main.go
     ```

2. **Configure reference sources**  
   - Update `config.yaml` or place API/config files in the expected locations to declare the packages, types, or components you want documented.

3. **Specify output format**  
   - The tool can emit HTML or Markdown. Use the `-f` / `--format` flag to select the output format:  
     ```bash
     ./genref -f markdown -include kubelet-config
     ```

4. **Customize templates**  
   - Edit templates under `html/` or `markdown/` to adjust formatting, sections, and front matter for generated output.

5. **Review outputs**  
   - Generated files are written to `output/html/` and/or `output/md/`. Inspect files for correct front matter and content before integrating into the website.

# Example cli usage

```bash
# Build and run genref to produce Markdown output for kubelet config types
cd genref
GO111MODULE=on make
./genref -f markdown -include kubelet-config
````

# Configuration and templates

* `config.yaml` controls which packages, types, and sections are included in generated output.
* HTML templates are located in `html/`; Markdown templates are located in `markdown/`. Customize templates to meet Kubernetes site front-matter and layout expectations.

# Todo

* Allow user to specify top-level structs.
* Add richer descriptions for each API/type.
* Mark packages used by the website so they can be treated differently from other versions.

