# wildfly-postgresql
add postgresql driver in wildfly server 
## creat folder org/posgresql/main
in wildfly server folder
- module.xml
```xml
<?xml version="1.1" encoding="UTF-8"?>
<module xmlns="urn:jboss:module:1.1" name="org.postgresql">
    <resources>
        <recource-root path="portgresql-42.7.1.jar"/>
    </resources>
    <depencencies>
        <module name="javax.api"/>
        <module name="javax.transaction.api"/>
    </depencencies>
</module>
```

- donwload postgresql driver put in org/postgresql/main
- create file module.xml in org/potgresql/main

folder structure
- wildfly-version
- -- org
- ---- postgresql
- ------ main
- ------- module.xml
- ------- postgresql-42.7.1.jar
## add resource configuration
- in /wildfly-version/standalone/configuration/standalone.xml 
```xml
...
        <subsystem xmlns="urn:jboss:domain:datasources:7.1">
            <datasources>
                <datasource jndi-name="java:jboss/datasources/PostgresDS" pool-name="PostgresDs">
                    <connection-url>jdbc:postgresql://localhost:5432/postgres</connection-url>
                    <driver>postgresql</driver>
                    <security>
                        <user-name>postgres</user-name>
                        <password>secreat</password>
                    </security>
                </datasource>
                <drivers>
                    <driver name="postgresql" module="org.postgresql">
                        <driver-class>org.postgresql.Driver</driver-class>
                    </driver>
                </drivers>
            </datasources>
        </subsystem>
...
```
