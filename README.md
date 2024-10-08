# Zipschema

Zipschema is a CLI tool for validating zipschema YAML files, validating 
ZIP file contents against these schemas, and generating documentation (Markdown or AsciiDoc).

Zipschema was written in order to allow for validation of "meta formats" which use the
zip file as a container.  While mostly these are loosely defined, this Zipschema was created
to allow for validation of those files, and the files they contain.



## Features

- **Schema Validation**: Validate the structure of your zipschema YAML file.
- **ZIP Validation**: Validate the contents of a ZIP file against a zipschema.
- **Documentation Generation**: Generate Markdown or AsciiDoc documentation from a zipschema.

## Installation

To install zipschema, run:

```bash
pip install zipschema
```

## Usage

### Validate a zipschema YAML file:

```bash
zipschema validate-schema path/to/zipschema.yaml
```

### Validate a ZIP file against a zipschema:

```bash
zipschema validate-zip path/to/zipschema.yaml path/to/zipfile.zip
```

### Generate documentation from a zipschema:

```bash
zipschema generate-docs path/to/zipschema.yaml --format markdown
```

## License

This project is licensed under the MIT License.
