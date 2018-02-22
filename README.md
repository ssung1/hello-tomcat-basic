Tomcat: Basic Sample
====================

### A Word about Tomcat

If the Tomcat installation is fresh, edit `conf/tomcat-users.xml` and add

```
<role rolename="manager-gui"/>
<role rolename="admin-gui"/>
<role rolename="manager-status"/>
<user username="tomcat" password="tomcat" roles="manager-gui, admin-gui, manager-status"/>
```

This enables the management console.

To start Tomcat, run
```
bin/catalina.sh run
```

Use a browser to view `http://localhost:8080`.  Port 8080 is the default.  If
that port does not work, check `conf/server.xml` to see what port is used.

### Building WAR File
1. Make sure Ant is installed and in PATH

2. To list all the tasks, do 
```
ant -p
```

3. See `build.xml` for a more detailed description of all the Ant tasks.

4. A typical deployment to Tomcat is through a WAR file.  To build the
WAR file, run
```
ant war
```

This builds `sample.war`.  If this file is not found, check the `war` target
in `build.xml`.

### Deploying WAR File
Copy the WAR file to `webapps` in the Tomcat installation directory.

### Testing the Web Application
Each web application has a context root.  By default, the context root is the
name of the WAR file excluding the .war extension.  In this case, the context
root would be `sample`.  To use a particular web application, use
```
http://{host}:{port}/{context root}
```
