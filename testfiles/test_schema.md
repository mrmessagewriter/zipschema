
# Sample Zip Schema

**Version:** 1.0.0

**Description:**

Image file formats have taken several forms over the years. 

Since 2003 they have generally been named .IS2 (Infrared Storage, version 2) for snapshot captures and .IS3 (Infrared Storage, version 3) for movie captures.

For IS2s, early camera designs used a binary serialization with hand-written code for encoding and decoding. These cameras are still in use, and the OpenAccess library has the code (and some small amount of documentation) for these files.

Since the launch of the Gemini cameras in 2013, a new version of IS2 format has been used, with some extensions added along the way. This format: - Uses .ZIP as a container for all of the following pieces.<br> - Internally stores visible light images and thumbnail images as .JPG or .PNG format files.<br> - Stores the infrared frame data as camera-specific BLOBs.<br> - Stores audio recordings as .WAV files<br> - Stores text input (notes, semi-structured annotations, asset tags & asset flags) as JSON or XML files<br> - Stores the metadata describing all of these pieces in a serialized form using the Google Protocol Buffer (gpb) library and tools.

 IS3 files have had two forms as well. <br> The first cameras to record IS3 movies were the Romulus design (~2012), and the file format was an extension of the older hand-written binary IS2, but including multiple IR and VL frames. The current version, launched in 2014 with a firmware release for Gemini, is based on the Matroska format, with audio, visible light and infrared frame tracks along with an "attachment" which consists of the same metadata from the .ZIP IS2 files.

This document references the IS2 Universal (IS2U).  This file is still labeled with the extension of ".is2" and is still uses the ZIP file as it's container. The main differences are related to the meta data, which has been moved from GPB files, into a single JSON file, named "info.json" which lives at the root of the zip file.

## File Tree
- root_text_file.txt
- config/
  - config.json
- docs/
  - readme.md
  - LICENSE
- images/
  - logo.png
  - logo.jpg
  - 
- temp/
  - *.tmp
- backup/
  - *.bak


## File List
| Filename | Summary | Section |
|----------|---------|---------|
| `root_text_file.txt` | this file exists in the root | Required Files |
| `config/config.json` |  | Required Files |
| `docs/readme.md` |  | Required Files |
| `docs/LICENSE` |  | Required Files |
| `images/logo.png` |  | Optional Logo Files |
| `images/logo.jpg` |  | Optional Logo Files |
| `temp/*.tmp` |  | Prohibited Files |
| `backup/*.bak` |  | Prohibited Files |
| `images/` |  | Directory Can Contain |

## Section List
### Required Files
These files are mandatory and must be present in the zip file.

#### allOf
- **`root_text_file.txt`**:  
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
### Directory Can Contain
This defines a directory which contains something, if it exists.

#### canContain
- **`images/`**: The 'images' directory, if present, should contain image files. 
    - Directory can contain the following:
      - **anyOf**:
          - `images/*.png`: PNG logo file.
          - `images/logo.jpg`: JPEG logo file.
