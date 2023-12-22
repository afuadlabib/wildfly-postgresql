# wildfly-postgresql
add postgresql driver in wildfly server 
## creat folder org/posgresql/main
in wildfly server folder
- module.xml
```xml
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
## add resource
- in /wildfly-version/standlone/configuration/standlone.xml 
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
