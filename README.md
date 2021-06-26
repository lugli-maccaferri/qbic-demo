# Qbic - manage your Minecraft servers with ease!
Qbic is a Minecraft servers manager written in Java, created with the main goal to pass the OOP exam in mind, but also to provide a free alternative to [Multicraft](https://multicraft.org), which can be very expensive for somebody who's just beginning to create their own Minecraft network.



# Authentication architecture description
Qbic is mainly based on *two* actors: the authserver and the instance.<br>
The authserver, as the name suggests, has the role of authenticating and validating users that make requests to the various instances, while the instances have the role of deploying and managing Minecraft servers.<br>
Both the authserver and the instances expose an HTTP REST API with various useful methods.
<br>
To initiate certain actions, users *must* provide a JWT token to the instance in question which, you guessed it, is provided and signed by the authserver with its  private key.
<br>
Instances are connected to a certain authserver and can verify and approve requests via the authentication schema described down below.
<br> 

a) Look for the `nodes` array in the authserver's `config.json` file (see [its page](https://github.com/lugli-maccaferri/qbic-demo/tree/main/authserver)):<br>
```
"nodes:" []
```
This object contains all the nodes (instances) that are connected to the authserver. The authserver will then send them its public key which will be used to verify the JWT token provided by the authserver.<br>
For example:
```
"nodes":  [  
	{  
		"name": "my fantastic server",  
		"host": "https://qbic.macca.cloud"  
	},  
	{  
		"name": "my home server",  
		"host": "http://10.8.0.2:3001"  
	}  
]
```
Note that each node is not only independent from the others, but also independent from the authserver. This is all the configuration you need to make an instance "talk" to the authserver (and back), the only thing you have to verify is the connectivity between authserver and instances;<br><br>
b) At boostrap time, the authserver will send to the specified nodes its public key (via HTTP);
<br><br>
c) Before initiating a request to a certain instance, a user **must** obtain a JWT token from the authserver (signed with the authserver's private key) with a simple [login request](https://github.com/lugli-maccaferri/qbic-demo/blob/main/authserver/api/auth.md#post-login);
<br><br>
d) The JWT token will look like this: 
```
{
  "is_admin": "1",
  "user_id": "cc178971-eb9f-416c-b5c3-6c9b7ff5366e",
  "edit_fs": "1",
  "iss": "qbic",
  "edit_others": "1",
  "exp": 1624560859,
  "iat": 1624553659,
  "username": "root"
}
```
This is all an instance needs to know about a user.
There's a lot more to know tho, dig deeper into configuration and stuff for more information.<br>

## Installation (never tested on Windows)
Make sure you have **at least** Java 14 installed<br>
`sudo apt install openjdk-14-jre`

### Qbic instance
First, make sure you have `sqlite3` installed:<br>
`sudo apt install sqlite3`<br>
Then, download the latest Qbic client release:<br>
`wget https://static.macca.cloud/qbic/client/lastest.jar -O qbic-client.jar`<br>
<br>
and basically, you're good to go! <br>
`java -jar qbic-client.jar`

### Qbic authserver
For the authserver, make sure you have whichever `mysql-server` version after 5.7 and generate a MySQL user and database:<br>
`sudo apt install mysql-server`<br>
**Important**: if you're running MySQL server >= 8.x make sure you set the authentication mode to `native` to the user you're using for Qbic, since `jasync-sql` has some troubles with other modes. [Here's how to do it.](https://medium.com/@crmcmullen/how-to-run-mysql-8-0-with-native-password-authentication-502de5bac661)
Then, download the latest Qbic authserver release:<br>
`wget https://static.macca.cloud/qbic/authserver/lastest.jar -O qbic-authserver.jar`<br>
and, again, everything is basically ready out of the box.

# Dig deeper into configuration and stuff
- [Qbic authserver](https://github.com/lugli-maccaferri/qbic-demo/tree/main/authserver)
- [Qbic instance](https://github.com/lugli-maccaferri/qbic-demo/tree/main/instance)
