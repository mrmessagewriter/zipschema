# ZIPSchema Format : v1.0.1

The `zipschema` format is a YAML-based schema used for defining, and validating the
contents of a zipfile *METAFORMAT*. It allows defining required, optional, 
and prohibited files, as well as the ability to validate individual 
files using JSON schemas or additional zipschemas.

This enables checking of JSONSchema, and ZipSchema files based
files in the zip file as well.   

Zipschema was created as a way to also generate documentation,
which more easily communicates the metaformat. Otherwise it's easy for developers
or AI's to get details wrong.

## Top-Level Fields

- **name**: A string representing the name of the schema.
- **description**: A string that describes the purpose of the schema.
- **version**: A string representing the schema version.
- **elements**: An array of objects that define the file structure and validation rules. Each object contains the following fields:

## Element Fields

### section_title
- **Type**: string
- **Description**: The title of the section (e.g., "Required Files", "Optional Files").

### section_description
- **Type**: string
- **Description**: A description of the section, explaining its purpose.

### allOf / anyOf / oneOf / noneOf / allowed
Each of these conditionals defines a list of file items. The conditionals have the following meanings:

- **allOf**: All files in the list must be present in the zip file.
- **anyOf**: At least one file from the list must be present.
- **oneOf**: Exactly one file from the list must be present.
- **noneOf**: Files in this list must not be present.
- **allowed**: These files are optional and will not be validated but will be documented.

Each file item in these conditionals has the following fields:

### path
- **Type**: string
- **Description**: The path of the file in the zip file.

### schema
- **Type**: string
- **Description**: Optional. Can be one of the following:
  - `self`: Indicates that the current zipschema should be applied to the specified file.
  - A path to a `zipschema`: Recursively validates the specified file using another zipschema.
  - A path to a `jsonschema`: Validates the specified file using a JSON schema.

### description
- **Type**: string
- **Description**: A description of the file and its purpose.

### summary
- **Type**: string
- **Description**: A brief summary of the file, which is used in documentation generation.
