# swagger-ui-auth-code-pkce-flow

To run the OAuth Authorization Code flow with PKCE using Swagger UI, a few customizations are required in the `index.html` file .
- `usePkceWithAuthorizationCodeGrant` should be set to `true` in the `ui.initOAuth` call. 
- A `requestInterceptor` function is added to remove `X-Requested-With` HTTP request header since sending a custom header transforms the CORS token request from simple to complex causing `OPTIONS` preflight request.


To run the example, please follow the steps : 
 ```bash 
git clone git@github.com:curityio/swagger-ui-auth-code-pkce-flow.git
  ```

```bash
cd swagger-ui-auth-code-pkce-flow
```

```bash
docker run -p 8080:8080 \
  -e BASE_URL=/swagger \
  -e API_URL=/swagger/swagger.yaml \
  -v $(pwd)/swagger.yaml:/usr/share/nginx/html/swagger.yaml \
  -v $(pwd)/index.html:/usr/share/nginx/html/index.html \
  swaggerapi/swagger-ui
```

Navigate to `http://localhost:8080/swagger` and click the `Authorize` button to initiate the OAuth code with pkce flow.

> **_NOTE:_**  Remember to add `http://localhost:8080/swagger/oauth2-redirect.html` as a redirect URI in your OAuth client configuration.
