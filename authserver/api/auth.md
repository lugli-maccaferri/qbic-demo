# Base endpoint `/auth`

#### POST `/login`
This request is used to obtain a signed JWT that you can then use to authorize requests to Qbic instances.
##### Parameters
|Name  |Type   | Description | Mandatory |
|--|--| -- | -- |
| `username ` | `string`  | The user's username | ✅|
| `password ` | `string`  | The user's password | ✅|
