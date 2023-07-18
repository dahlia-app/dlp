# v1.0.0
DLP files are traditional zip archives, that is how they should be read

## Config
The basic config for the project is contained in an entry named `.config`. It is a JSON file containing the following fields:

### Config
| Field | Type | Description | Example
|---|---|---|---|
| name | String | The name of the project | "New Project" |
| description | String? | Project description | "A basic Dahlia project" |
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
  "description": null
  "saveResponses": false,
  "version": null,
  "type": 0
}
```

## Variables
Project level variables are stored in an entry named `.vars`, they are stored as a JSON map with the name of the variable as the key and the properties as the value. A variable object is shown below: 

### Variable
| Field | Type | Description | Example |
|---|---|---|---|
| value | String | The value assigned to this variable | "https://api.github.com" |
| sensitive | Boolean | Whether this variable is sensitive, like a user token or password | false |

Ex.
```json
{
  "baseUrl": {
    "value": "https://api.github.com",
    "sensitive": false
  }
}
```

## Requests
Requests can have any name as long as it ends in `.req`, they are also stored as JSON.

### Request
| Field | Type | Description | Example |
|---|---|---|---|
| method | Enum (One of GET, POST, PUT, PATCH, HEAD, or DELETE) | The method used for the HTTP request | "GET"
| name | String | The name of the request | "Get user" |
| description | String? | Description of this request | "Gets a specific user by id" |
| folder | Int | The id of the [folder](#folder) that this request belongs to (1 being the root) | 2 |
| url | String | The url of this request | "https://example.com/users/{id}" |
| queries | Map<String, String> | The query parameters to be appended to the url | { "q": "some query" } |
| headers | Map<String, String> | The headers to be used on the request | { "content-type": "application/json" } |
| variables | Map<String, [Variable](#variable)> | Variables specific to this request, overrides any project variables that share names | { "id": { "value": "123456789", "sensitive": false } } |
| body | String? | The body to be sent along with the request | "{ "username": "wing" }" |

Ex.
```json
{
  "method": "GET",
  "name": "Get user",
  "description": "Get a user by id",
  "folder": 2,
  "url": "https://example.com/users/{id}",
  "queries": {},
  "headers": {
    "authorization": "Bearer ABCDEFGHIJ"
  },
  "variables": {
    "id": {
      "value": "1234567890",
      "sensitive": false,
    }
  },
  "body": null
}
```

## Folders
Folder entries can be any name as long as they end in `.folder`, they are also JSON files

## Folder
| Field | Type | Description | Example |
|---|---|---|---|
| id | Int | The id of the folder (May not be 1 as that corresponds to the root) | 2 |
| name | String | The name of the folder | "Users" |

Ex.
```json
{
  "id": 2,
  "name": "Users"
}
```
