```
 _       ___ __    __________         ____ 
| |     / (_) /___/ / ____/ /_  __   ( __ )
| | /| / / / / __  / /_  / / / / /  / __  |
| |/ |/ / / / /_/ / __/ / / /_/ /  / /_/ / 
|__/|__/_/_/\__,_/_/   /_/\__, /   \____/  
                         /____/            
```

Summary
=======

This is a jboss install for running <a href="https://github.com/mgijax/ServerMonitoring">Server Monitoring</a> which takes in data from <a href="https://github.com/mgijax/WatchDog">Watch Dog Clients</a> and stores it in the database defined in dbconfig.properties.

Installation / Configuration
============================

```
> git clone git@github.com:mgijax/wildfly-8.2.0-servermonitoring.git
> cd wildfly-8.2.0-servermonitoring.git
> vim Install
```

Change the values for the admin user it will be created as admin:admin highly suggested that that be changed from the default. 

```
./bin/add-user.sh admin admin
```
Once the values have been changed run the install script:
```
> ./Install
```
Next edit the dbconfig.properties file, this will be the data credentials for connecting to a postgres database.
```
> vim dbconfig.properties

db.database=DataBaseName
db.hostname=localhost
db.username=usernam3
db.password=p4ssword
api.hostname=localhost
```
Set the api.hostname equal to the hostname that you will be running this server on, and this will also be the name that the <a href="https://github.com/mgijax/WatchDog">Watch Dog Clients</a> are going to try to connect to.

Running the server
==================

Start the server like any other jboss instance, this can be done by running it on a screen or putting it to the background and then logging out.
```
> ./bin/standalone.sh -P=dbconfig.properties
```

Connecting to the server
========================

To connect to the server goto http://api.hostname/ and for all the connected clients you will see a graph that is updating in realtime for the data that they are sending.
Also the API is viewable via http://api.hostname/api.




