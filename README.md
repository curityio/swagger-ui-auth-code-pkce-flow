Swagger UI with OAuth Authorization Code Flow (PKCE)

This repository demonstrates how to customize Swagger UI to support the OAuth Authorization Code flow with PKCE.

**Customizations**

**Enable PKCE**:

Set `usePkceWithAuthorizationCodeGrant` to `true` in the `ui.initOAuth` call in the `index.html` file.

**Request Interceptor**:

Add a `requestInterceptor` function to remove the `X-Requested-With` HTTP request header. This prevents the CORS token request from being transformed into a complex request, which would trigger an `OPTIONS` preflight.


**Usage**

Follow these steps to run the example:

1. Clone the repository:
    ```bash
    git clone git@github.com:curityio/swagger-ui-auth-code-pkce-flow.git
    ```

2. Navigate to the project directory:
    ```bash
    cd swagger-ui-auth-code-pkce-flow
    ```

3. Start the Swagger UI container:
    ```bash
    docker run -p 8080:8080 \
      -e BASE_URL=/swagger \
      -e API_URL=/swagger/swagger.yaml \
      -v $(pwd)/swagger.yaml:/usr/share/nginx/html/swagger.yaml \
      -v $(pwd)/index.html:/usr/share/nginx/html/index.html \
      swaggerapi/swagger-ui
    ```

4. Open your browser and go to:
    [http://localhost:8080/swagger](http://localhost:8080/swagger)

5. Click the Authorize button to initiate the OAuth Authorization Code flow with PKCE.

> **_NOTE:_** Ensure that http://localhost:8080/swagger/oauth2-redirect.html is added as a redirect URI in your OAuth client configuration