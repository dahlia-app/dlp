# v1.0.0
DLP files are traditional zip archives, that is how they should be read

## Config
The basic config for the project is contained in an entry named `.config`. It is a JSON file containing the following fields:

### Config
| Field | Type | Description | Example
|---|---|---|---|
| name | String | The name of the project | "New Project" |
| description | String | Project description | "A basic Dahlia project" |
| version | String? | Version of the project | "v1" |
| saveResponses | Boolean | Whether to save responses to disk automatically | true |
| type | [Type](#type) (Integer) | The type of project* | 0 |

### Type
| Name | Ordinal | Description |
|---|---|---|
| normal | 0 | A regular Dahlia project |
| request | 1 | Special project designed to only hold one request |

Ex. 
```json
{
  "name": "GitHub",
  "description": "Some github requests"
  "saveResponses": false,
  "version": null,
  "type": 0
}
```

## Variables
Project level variables are stored in an entry named `.vars`, they are stored as a JSON map with the name of the variable as the key and the properties as the value. A variable object is shown below: 

### Variable
| Field | Type | Description | Example
|---|---|---|---|
| value | String | The value assigned to this variable | "https://api.github.com"
| sensitive | Boolean | Whether this variable is sensitive, like a user token or password | false

Ex.
```json
{
  "baseUrl": {
    "value": "https://api.github.com",
    "sensitive": false
  }
}
```
