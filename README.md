# Saponoso

A Python tool for calling SAP RFCs via SOAP and parsing responses into Python dictionaries.

## Usage

### Prerequisites
- Python 3.7+
- Install dependencies:
  ```sh
  pip install httpx lxml
  ```

### Environment Variables
You can set credentials and endpoints using environment variables:
- `SAP_USERNAME`: SAP username
- `SAP_PASSWORD`: SAP password
- `SAP_ENDPOINT_PRO`: SAP production endpoint URL
- `SAP_ENDPOINT_QAS`: SAP QA endpoint URL

### Command Line Arguments
```
python saponoso.py [options]
```

#### Options
- `--endpoint ENDPOINT`   : SAP endpoint key (`pro` or `qas`). Defaults to `qas`.
- `--username USERNAME`   : SAP username (or set `SAP_USERNAME` env var)
- `--password PASSWORD`   : SAP password (or set `SAP_PASSWORD` env var)
- `--rfc RFCNAME`         : RFC name to call (default: `STFC_CONNECTION`)
- `--params JSON_STRING`  : RFC parameters as JSON string (default: `{}`)
- `-f, --file FILE`       : JSON file containing RFC parameters
- `--introspect`          : Show introspection of response variables
- `--pretty-xml`          : Show response as pretty-printed XML
- `--debug`               : Enable debug output

### Example
```sh
python saponoso.py --endpoint qas --username myuser --password mypass --rfc ZRFC_EXAMPLE --params '{"I_USER": "ASTANFIELD"}'
```
Or using environment variables:
```sh
set SAP_USERNAME=myuser
set SAP_PASSWORD=mypass
python saponoso.py --rfc ZRFC_EXAMPLE --params '{"I_USER": "ASTANFIELD"}'
```
Or with a JSON file:
```sh
python saponoso.py --rfc ZRFC_EXAMPLE -f params.json
```

### Output
The parsed result will be printed as a Python dictionary. Table variables are returned as lists of dictionaries under the `'type': 'table'` key.

---
See the source code for more details and advanced usage.
