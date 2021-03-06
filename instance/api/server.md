
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
<br>

#### POST `/start/:server_id`
This request is used to start a server given its id (**note that the server id must be an URL parameter, not a body parameter**)
##### Parameters
None.
<br>
The response will be successful even if the server process encounters some sort of error, since the HTTP response reflects the status of the HTTP transaction (that's also done because the server runs parallel to the request, so the webserver doesn't have to wait the server to start - and potentially fail).
<br>To check server health, take a look at /server/info/:id (you can also check console output via websocket).<br>

##### Example response (success):
```
{
	success: true
}
```
<br>


#### GET `/files/:id`
This request is used to scan a server main folder given its id.
<br>
Basically you'll get the server root with its files.
##### Parameters
None.
<br>

##### Example response (success):
```
{
	"is_directory": true,
	"success": true,
	"content": [
		"eula.txt",
		"server.jar",
		"server.properties"
	]
}
```
<br>

#### GET `/files/:id/:path`
This request is used to read a path inside the server root.<br>
**Important**: the `path` parameter **must be the base64 encode** of the path you want to read.<br>
For example: if the resource needed is `eula.txt`, the request URL must be <br>
`/files/:id/ZXVsYS50eHQ=`.
<br> As you can tell, the last parameter is the base64 encode of the string `eula.txt`.<br>
If the file is inside a folder you just have to encode the full path.<br>
For example:  if the resource needed is `eula.txt`,  in the folder `items` the request URL must be <br>
`/files/:id/aXRlbXMvZXVsYS50eHQ=`, which is the base64 encode of `items/eula.txt`
<br>
If the requested resource is a directory, the response will contain a list of its files (similar to `/files/:id`)
<br>
##### Parameters
None.
<br>

##### Example response (success):
```
{
	"is_directory": false,
	"success": true,
	"content": "eula=true"
}
```
**Note**: `content` is the content of the file you're seeing. If the path is a directory (`is_directory: true`), `content` will contain the contents of such directory.

<br>


#### GET `/list`
This request is used to list all the Minecraft servers that the current node is handling
##### Parameters
None.
<br>

##### Example response (success):
```
{
  "servers": [
    {
      "owner": "cc178971-eb9f-416c-b5c3-6c9b7ff5366e",
      "name": "serveruccio",
      "id": "Nfb5Y71QtUDKyyaqEv0UxbRqYLVaF8zg"
    }
  ],
  "success": true
}
```
<br>

#### GET `/info/:id`
This request retrieves info from a server given its ID with the ([Minecraft query protocol](https://wiki.vg/Query))
##### Parameters
None.
<br>

##### Example response (success):
```
{
  "motd": "A Minecraft Server",
  "main_world": "world",
  "success": true,
  "max_players": 20,
  "gamemode": "SMP",
  "online_players": 0
}
```
<br>


#### POST `/send-command/:id`
This request sends a command to aserver given its ID with the ([RCON protocol](https://developer.valvesoftware.com/wiki/Source_RCON_Protocol)).
**Remember to omit the "/" then sending the command**

##### Parameters
|Name  |Type   | Description | Mandatory |
|--|--| -- | -- |
| `command ` | `string`  | A Minecraft command | ✅|

<br>

##### Example response (success):
```
{

	"command_response": "Set the time to 1000",
	"success": true

}
```
(The command was `time set day`).
<br>


#### POST `/stop/:id`
This request stops a server given its ID.
#### Parameters 
None.
<br>

##### Example response (success):
```
{

	"success": true
}
```
