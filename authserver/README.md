# The authserver
Hey there, now that you read the whole introduction thing, you're ready to know more about the authserver.<br>
Basically, all the authserver does is **authenticating users and signing JWTs**. Yeah, that's really it.
<br>
Because the infrastructure is "*as scalable as we could make it*", the authserver is connected to a MySQL database that contains all the user data (with "all" i mean the username, the password and their permissions on the nodes).
<br>
The first time is started, the authserver generates its public/private RSA keypair, which will be used to authenticate requests to instances.
# Configuration
The configuration is pretty simple and self explanatory:
```
{  
	"jwt_timeout": 7200,  
	"mysql":  {  
		"host": "localhost",  
		"username": "qbic_user",  
		"password": "qbic_pass",  
		"database": "qbic",  
		"port": 3306  
	},  
	"nodes":  [  
		{  
			"name": "mc1",  
			"host": "https://qbic.macca.cloud"  
		},  
		{  
			"name": "hp-envy",  
			"host": "http://10.8.0.2:3001"  
		}  
	]  
}
```
`jwt_timeout` is the interval, in seconds, during which the generated JWTs will be valid. <br>
I think you can guess what the `mysql` object is for and we already talked about the `nodes` section, so we can move on and discuss some other matters.
