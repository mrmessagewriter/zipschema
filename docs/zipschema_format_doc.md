
# Zipschema Documentation with Examples

This document describes the fields of the `zipschema`, a schema for validating the contents of ZIP files, along with examples.

## Top-level Fields

### `name` (string)
- **Description**: The name of the zipschema.
- **Example**:
    ```yaml
    name: "Sample Zip Schema"
    ```

### `description` (string)
- **Description**: A description of the zipschema.
- **Example**:
    ```yaml
    description: "A schema for validating zip files containing project configurations."
    ```

### `version` (string)
- **Description**: The version number of the zipschema.
- **Example**:
    ```yaml
    version: "1.0.0"
    ```

### `elements` (array)
- **Description**: A list of elements that define the structure and constraints for the files inside the ZIP archive.
- **Example**:
    ```yaml
    elements:
      - section_title: "Required Files"
        section_description: "These files must be present."
        allOf:
          - path: "config/config.json"
          - path: "docs/README.md"
    ```

## Element Fields

Each element in the `elements` array can contain the following fields:

### `section_title` (string)
- **Description**: The title of the section for this set of conditions.
- **Example**:
    ```yaml
    section_title: "Required Files"
    ```

### `section_description` (string)
- **Description**: A description of the section.
- **Example**:
    ```yaml
    section_description: "These files are mandatory and must be present in the zip file."
    ```

### `allOf` (array)
- **Description**: A set of files that must all be present.
- **Items**: Each item in the `allOf` array is an object that describes a file.
- **Example**:
    ```yaml
    allOf:
      - path: "config/config.json"
      - path: "docs/README.md"
    ```

### `anyOf` (array)
- **Description**: At least one of the files in this list must be present.
- **Items**: Each item in the `anyOf` array is an object that describes a file.
- **Example**:
    ```yaml
    anyOf:
      - path: "images/logo.png"
      - path: "images/logo.jpg"
    ```

### `oneOf` (array)
- **Description**: Exactly one file from this list must be present.
- **Items**: Each item in the `oneOf` array is an object that describes a file.
- **Example**:
    ```yaml
    oneOf:
      - path: "data/dataset.csv"
      - path: "data/dataset.json"
    ```

### `noneOf` (array)
- **Description**: None of the files in this list should be present.
- **Items**: Each item in the `noneOf` array is an object that describes a file.
- **Example**:
    ```yaml
    noneOf:
      - path: "temp/*.tmp"
      - path: "backup/*.bak"
    ```

### `allowed` (array)
- **Description**: A set of optional files that are allowed but not required.
- **Items**: Each item in the `allowed` array is an object that describes a file.
- **Example**:
    ```yaml
    allowed:
      - path: "logs/logfile.txt"
      - path: "reports/report.pdf"
    ```

## File Item Fields

Each file in the `allOf`, `anyOf`, `oneOf`, `noneOf`, or `allowed` arrays is an object that can contain the following fields:

### `path` (string)
- **Description**: The file path or pattern to match files inside the ZIP archive.
- **Example**:
    ```yaml
    path: "config/config.json"
    ```

### `title` (string)
- **Description**: The title of the file.
- **Example**:
    ```yaml
    title: "Configuration File"
    ```

### `description` (string)
- **Description**: A description of the file.
- **Example**:
    ```yaml
    description: "The main configuration file for the project."
    ```

### `schema` (string)
- **Description**: A reference to an external schema that should be used to validate this file.
- **Example**:
    ```yaml
    schema: "config_schema.json"
    ```

### `link` (string)
- **Description**: A link to the file, either a URL or a path for documentation purposes.
- **Example**:
    ```yaml
    link: "https://example.com/config-schema"
    ```

## Required Fields

The following fields are required in the `zipschema`:
- `name`
- `description`
- `version`
- `elements`

Each `fileItem` object must include the `path` field.

- **Example of a full zipschema**:
    ```yaml
    name: "Sample Zip Schema"
    description: "A schema for validating zip files containing project configurations."
    version: "1.0.0"
    elements:
      - section_title: "Required Files"
        section_description: "These files must be present."
        allOf:
          - path: "config/config.json"
            title: "Configuration File"
            description: "The main configuration file."
            schema: "config_schema.json"
          - path: "docs/README.md"
            title: "README File"
            description: "The project documentation."
      - section_title: "Optional Files"
        section_description: "These files are optional but can be included."
        allowed:
          - path: "logs/logfile.txt"
          - path: "reports/report.pdf"
    ```