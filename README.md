# MD-Models Example repository

This repository contains an example of how markdown models and the corresponding [MD-Models](https://github.com/JR-1991/md-models) Rust library can be used to orchestrate the generation of multiple formats, code and documentation from a single source of truth. The repository contains the following parts:

- `specifications`: Contains the markdown models that define the structure of the data model.
- `schemes`: Contains multiple schema targets which are derived from the markdown models.
- `python`: Contains the python code that is generated from the markdown models.

## Using `gen.toml`

The `gen.toml` file contains the configuration for the generation of the different targets. Here you can specify which generation targets you want to have. The file is structured as follows:

```toml
[meta]
name = "EnzymeML"
description = "Generate Python classes, documentation and various schemes from a markdown model"
paths = ["specifications/enzymeml.md"]

[generate]
shex = { out = "schemes/enzymeml.shex" }
json-schema = { out = "schemes/enzymeml.json", root = "EnzymeMLDocument" }
xml-schema = { out = "schemes/enzymeml.xsd" }
python-dataclass = { out = "python/pyenzyme/models.py" }
mk-docs = { out = "docs/model.md" }
```
