# Steeltoe-EFCore-API

A simple example using Steeltoe with Entity Frameword Core along with the reccomended packages for microservices.

## Packages Included

- *Steeltoe.Connector.EFCore*: manages the connection with the SQL database

- *Steeltoe.Management.EndpointCore*: provides the boilerplate microservice stuff like health endpoint, enhanced logging features, info endpoint, etc

- *Steeltoe.Management.TracingCore*: enhances application with automatic generation of space and trace data and also formats data to be zipkin compatible

## About EF Core Connection

The application has a dbcontext called TodoItems. Within is a model for a TodoItem. Have a look at `appsettings.json` and note the `SqlServer:Credentials` area. That is where you specify where the database is hosted, the database name, and possible creds.

Currently this application is expecting the Visual Studio hosted LocalDB to be available when starting. If it isn't the application will complain and not start.

Optionally you could comment out the `ConnectionString` and uncomment the other values to a different SQL server. To see more configuration options [read the docs](https://steeltoe.io/docs/3/connectors/microsoft-sql-server).

## Using Project Tye

The application was developed in Visual Studio 2019 and is meant to be run through that debugger, using LocalDB. If you would like to unlock more features from the app, there is a [project tye](https://github.com/dotnet/tye) manifest provided that will spin up a MSSQL database as well as a Zipkin server.

To use the app with Tye:
- Comment out `ConnectionString` and uncomment the other values. No need to change anything they are ready to go.
- In your terminal of choice `cd` to the project folder and start tye `tye run`
- Then run the application in Visual Studio like normal (F5)

## Adding in Spring Boot Admin

The project also has provisions for connecting with a [Spring Admin server](https://github.com/codecentric/spring-boot-admin) dashboard. To unlock this feature you'll need to use the above project tye hosting option.

- Uncomment the Spring Admin feature in `tye.yaml`
- Run tye as described above
- Uncomment the `RegisterWithSpringBootAdmin` statement in `Startup.cs`
- Uncomment the Spring Admin feature in `appsettings.json`
- Run the application in Visual Studio like normal (F5)
