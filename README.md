# Qbic - manage your Minecraft servers with ease!
Qbic is a Minecraft servers manager written in Java, created with the main goal to pass the OOP exam in mind; but also to provide a free alternative to [Multicraft](https://multicraft.org), which can be very expensive for somebody who's just beginning to create their own Minecraft network.

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
For the authserver, make sure you have whichever `mysql-server` version after 5.7:<br>
`sudo apt install mysql-server`.
Generate a MySQL user and database.<br>
**Important**: if you're running MySQL server >= 8.x make sure you set the authentication mode to `native` to the user you're using for Qbic, since `jasync-sql` has some troubles with other modes. [Here's how to do it.](https://medium.com/@crmcmullen/how-to-run-mysql-8-0-with-native-password-authentication-502de5bac661)
Then, download the latest Qbic authserver release:<br>
`wget https://static.macca.cloud/qbic/authserver/lastest.jar -O qbic-authserver.jar`<br>
and, again, everything is basically ready out of the box.

# Dig deeper into configuration and stuff
- Qbic instance
- Qbic authserver

# REST APIs
- Qbic instance
- Qbic authserver
