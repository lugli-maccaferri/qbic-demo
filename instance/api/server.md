
# Base endpoint `/server`

#### POST `/create`
This request is used to create a new server.<br>
Note that the request will be successful **only if the user who is making it has the "edit_fs" permission**.
##### Parameters
|Name  |Type   | Description | Mandatory |
|--|--| -- | -- |
| `name ` | `string`  | The server's name | ✅|
| `query-port ` | `short`  | The server's query port (used to get info about the server) | ✅|
| `server-port ` | `short`  | The server's TCP port (used to connect to the server) | ✅|
| `rcon-port ` | `short`  | The server's TCP port (used to connect to the server) | ✅|
| `xmx ` | `string`  | Max RAM allocated to the server | ❌ (default 1G) |
| `xms ` | `string`  | Minimum RAM allocated to the server | ❌ (default 1G) |
| `jar_path ` | `string`  | Server's jar path, can be local or a URL | ❌ (default https://static.macca.cloud/qbic/jars/spigot.jar) |
<br>

A note about the `jar_path` parameter: Qbic provides a `jars` folder in its root directory where you can upload all your custom jars. When specifying a local jar you just need to input its name which then will be searched in the `jars` folder.<br>
For example, if you upload a jar named `my-spigot.jar` and you want to use it for a server you just need to input `my-spigot.jar` as the `jar_path` parameter.

<br>

##### Example response (success):
```
{
	"server": {
		"owner": "cc178971-eb9f-416c-b5c3-6c9b7ff5366e",
		"name": "serveruccio",
		"id": "Nfb5Y71QtUDKyyaqEv0UxbRqYLVaF8zg"
	},
	"success": true
}
```
