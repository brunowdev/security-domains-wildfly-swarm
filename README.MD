### Security Domains Example

This project shows how to use a custom Security Domain to encrypt your DB password without exposing it in your configuration files.

You can also use the logic on `yaml` for Oracle Db.

**Step 1:**

You can run Postgresql with docker or just use your running instance. If you choose an existing instance, check your pass and database name.

```jshelllanguage
docker run -e POSTGRES_PASSWORD=yourDbPass -d -p 5432:5432 postgres
``` 

**Step 2:**

To encrypt an DB pass with picketbox, just run the jar file inside the jars folder passing the following paramters:

```jshelllanguage
java -cp picketbox-5.0.2.Final.jar org.picketbox.datasource.security.SecureIdentityLoginModule yourDbPass
``` 

**Step 3:**

Update the DB `password` property on yaml file with your encrypted password

**Step 4:**

Run the example:

```
mvn wildfly-swarm:run
```

Check if is connect by accessing localhost:8080

```
Howdy using driver: PostgreSQL JDBC Driver
```

The `project-defaults-exposing-password.yaml` file is the same yaml file without configuring a security domain.
