# Base endpoint `/auth`

#### GET `/`
This request is used to obtain info about the current JWT (basically user information).
##### Parameters
None.<br>
##### Example response (success):
```
{
	"success": true,
	"user": {
		"is_admin": 1,
		"user_id": "cc178971-eb9f-416c-b5c3-6c9b7ff5366e",
		"edit_fs": 1,
		"iss": "qbic",
		"edit_others": 1,
		"username": "root"
	}
}
```
