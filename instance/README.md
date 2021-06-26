
# The instance
Let's see what the instance is capable of.<br>
Basically, instances are the "workers" of the architecture. On instances you can deploy and manage multiple Minecraft servers without worrying about anything concerning the authserver and other difficult and boring matters. The only thing you need to be sure of is, again, the connectivity between an instance (or *node*) and the authserver.

# Configuration
The configuration is much simpler, all you need to do is to specify the name of the node and its parent.
<br>For example:
```
{
	"name": "my awesome server",
	"parent": "https://authserver.macca.cloud"
}
```
**Important**: the parent value **must** be a FQDN (fully qualified domain name) in order to be verified when its public key will be sent.

# More stuff about instances
Instances are meant to be as standalone and autonomous as possible. When you first start an instance an `sqlite3` database file will be created and initialized (TODO: upload the schema).
<br>
Once the instance has successfully started you can use the REST API and its methods simply providing the JWT in the `Authorization` header as a Bearer token (more info in the [dedicated page](https://github.com/lugli-maccaferri/qbic-demo/blob/main/instance/api/auth.md))
