
# Sample Zip Schema

**Version:** 1.0.0

**Description:**

A sample schema for validating zip files, including various conditionals, schema references, and file patterns.

Description Line 2

## File Tree
- config/
  - config.json
- docs/
  - readme.md
  - LICENSE
- images/
  - logo.png
  - logo.jpg
- temp/
  - *.tmp
- backup/
  - *.bak


## File List
| Filename | Summary | Section |
|----------|---------|---------|
| `config/config.json` |  | Required Files |
| `docs/readme.md` |  | Required Files |
| `docs/LICENSE` |  | Required Files |
| `images/logo.png` |  | Optional Logo Files |
| `images/logo.jpg` |  | Optional Logo Files |
| `temp/*.tmp` |  | Prohibited Files |
| `backup/*.bak` |  | Prohibited Files |

## Section List
### Required Files
These files are mandatory and must be present in the zip file.

#### allOf
- **`config/config.json`**: The main configuration file for the application. 
- **`docs/readme.md`**: The README file provides an overview of the project. 
- **`docs/LICENSE`**: The LICENSE file contains the legal terms for using this project. 
### Optional Logo Files
At least one of the following logo files must be present.

#### anyOf
- **`images/logo.png`**: The PNG format logo image. 
- **`images/logo.jpg`**: The JPEG format logo image. 
### Prohibited Files
These files must not be present in the zip file.

#### noneOf
- **`temp/*.tmp`**: Temporary files that should not be included in the zip file. 
- **`backup/*.bak`**: Backup files that should not be included in the zip file. 
