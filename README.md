# security-openid-connect-quickstart

This project demonstrates an app that uses the Quarkus OIDC authorization code flow.

This app, at the `/callback` URI, will generate a 302 redirect with two `Location` headers. Several other headers (`Pragma` and `Cache-Control`) are also duplicated, but the Location header is the one that will trip up Safari.

One can build this project with the following command:

```
./mvnw package
```

Three configuration values will need to be added to a `./config/application.properties` file, based on, for instance a running KeyCloak server.

```
quarkus.oidc.auth-server-url=<https://idp.example>
quarkus.oidc.client-id=<example-client-id>
quarkus.oidc.credentials.secret=<example-client-secret>
```

The application will run at `http://localhost:8080`. By opening the network tab of a browser and filtering on `callback`, one can see the duplicated headers.

When using Safari, the authentication flow does not complete successfully.
