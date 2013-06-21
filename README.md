
# Introduction

The drop wizard example application was developed to, as its name implies, provide examples of some of the features
present in drop wizard.

# Overview

Included with this application is an example of the optional db API module. The examples provided illustrate a few of
the features available in [JDBI](http://jdbi.org), along with demonstrating how these are used from within dropwizard.

This database example is comprised of the following classes.

* The `PersonDAO` illustrates using the [SQL Object Queries](http://jdbi.org/sql_object_api_queries/) and string template
features in JDBI.

* The `PeopleDAO.sql.stg` stores all the SQL statements for use in the `PersonDAO`, note this is located in the
src/resources under the same path as the `PersonDAO` class file.

* `migrations.xml` illustrates the usage of `dropwizard-migrations` which can create your database prior to running
your application for the first time.

* The `PersonResource` and `PeopleResource` are the REST resource which use the PersonDAO to retrieve data from the database, note the injection
of the PersonDAO in their constructors.

As with all the modules the db example is wired up in the `initialize` function of the `HelloWorldApplication`.

# Running The Application

To test the example application run the following commands.

* To package the example app:

        mvn package

* To setup the h2 database:

        java -jar target/dropwizard-example-0.7.0-SNAPSHOT.jar db migrate example.yml

* To run the server:

        java -jar target/dropwizard-example-0.7.0-SNAPSHOT.jar server example.yml

# Adding The AppDynamics Java Agent

* Download the AppDynamics Java Agent from the SAAS controller

        unzip appagent.zip -d /opt/appdynamics/java-agent

* To run the server with the appdyanmics java agent:

        java -javaagent:/opt/appdynamics/java-agent/javaagent.jar -jar target/dropwizard-example-0.7.0-SNAPSHOT.jar server example.yml

