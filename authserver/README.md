# The authserver
Now that you read the introduction, you are ready to know more about the authserver.<br>
Fundamentally, all the authserver does is authenticating users and signing JWTs.<br>
Since the infrastructure is "*as scalable as we could make it*", the authserver is connected to a MySQL database that contains all the user data: the username, the password and the permissions on the nodes.<br>
When the authserver is started for the first time, it generates its public/private RSA keypair, which is then used to authenticate requests to instances.
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
We already talked about the nodes section and you can guess what the mysql object does/is for, therefore we can move on and discuss other matters.

# [Read the API docs for the authserver!](https://github.com/lugli-maccaferri/qbic-demo/tree/main/authserver/api)
