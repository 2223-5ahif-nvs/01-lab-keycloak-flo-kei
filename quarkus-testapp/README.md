# security-keycloak-authorization-quickstart Project

This project uses Quarkus, the Supersonic Subatomic Java Framework.

If you want to learn more about Quarkus, please visit its website: https://quarkus.io/ .

## Running the application in dev mode

You can run your application in dev mode that enables live coding using:
```shell script
./mvnw compile quarkus:dev
```

> **_NOTE:_**  Quarkus now ships with a Dev UI, which is available in dev mode only at http://localhost:8080/q/dev/.

## Packaging and running the application

The application can be packaged using:
```shell script
./mvnw package
```
It produces the `quarkus-run.jar` file in the `target/quarkus-app/` directory.
Be aware that it’s not an _über-jar_ as the dependencies are copied into the `target/quarkus-app/lib/` directory.

The application is now runnable using `java -jar target/quarkus-app/quarkus-run.jar`.

If you want to build an _über-jar_, execute the following command:
```shell script
./mvnw package -Dquarkus.package.type=uber-jar
```

The application, packaged as an _über-jar_, is now runnable using `java -jar target/*-runner.jar`.

## Creating a native executable

You can create a native executable using: 
```shell script
./mvnw package -Pnative
```

Or, if you don't have GraalVM installed, you can run the native executable build in a container using: 
```shell script
./mvnw package -Pnative -Dquarkus.native.container-build=true
```

You can then execute your native executable with: `./target/security-keycloak-authorization-quickstart-1.0.0-SNAPSHOT-runner`

If you want to learn more about building native executables, please consult https://quarkus.io/guides/maven-tooling.

## Related Guides

- OpenID Connect ([guide](https://quarkus.io/guides/security-openid-connect)): Verify Bearer access tokens and authenticate users with Authorization Code Flow
- Keycloak Authorization ([guide](https://quarkus.io/guides/security-keycloak-authorization)): Policy enforcer using Keycloak-managed permissions to control access to protected resources

## Additional notes

https://auth.flokei.at/realms/master/broker/oidc/endpoint

https://auth.flokei.at/realms/master/.well-known/openid-configuration

https://auth.flokei.at/realms/quarkus/protocol/openid-connect/token


export access_token=$(\
curl --insecure -X POST https://auth.flokei.at/realms/quarkus/protocol/openid-connect/token \
--user backend-service:secret \
-H 'content-type: application/x-www-form-urlencoded' \
-d 'username=alice&password=alice&grant_type=password' | jq --raw-output '.access_token' \
)

https://quarkus.io/guides/security-keycloak-authorization#testing-the-application

curl -v -X GET \
http://localhost:8080/api/users/me \
-H "Authorization: Bearer "$access_token

localhost:8080/q/dev
http://localhost:8080/q/dev/io.quarkus.quarkus-oidc/provider

localhost:8080/api/users/me
localhost:8080/api/admin

username:
alice

password:
alice

loginpage:
https://lists.jboss.org/pipermail/keycloak-user/2016-July/007045.html
https://auth.flokei.at/realms/quarkus/protocol/openid-connect/auth?client_id=backend-service&response_mode=fragment&response_type=code&login=true&redirect_uri=localhost:8080/api/users/me

deploy keycloak with pre-made realm:
https://stackoverflow.com/questions/54796791/importing-keycloak-configuration-files-while-using-docker-compose

quarkus realm file:
https://raw.githubusercontent.com/quarkusio/quarkus-quickstarts/main/security-keycloak-authorization-quickstart/config/quarkus-realm.json