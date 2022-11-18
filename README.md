# Basic CRUD with Vue.js and Node

This example app shows how to create a Node.js API and display its data with a Vue.js UI.

**Prerequisites:** [Node.js](https://nodejs.org/).

* [Getting Started](#getting-started)
* [Links](#links)
* [Help](#help)
## Getting Started

To install this example application, run the following commands:

```bash
git clone https://github.com/LeoJinDev/vue-node.git
cd vue-node
npm install
```

This will get a copy of the project installed locally. To start each app, follow the instructions below.

To run the server:

```bash
node ./src/server
```

To run the client:

```bash
npm run dev
```

### Create an Application in Okta

You will need to [create an OpenID Connect Application in Okta](https://developer.okta.com/blog/2018/02/15/build-crud-app-vuejs-node#add-authentication-with-okta) to get your values to perform authentication.

Before you begin, you’ll need a free Okta developer account. Install the [Okta CLI](https://cli.okta.com/) and run `okta register` to sign up for a new account. If you already have an account, run `okta login`.

Then, run `okta apps create`. Select the default app name, or change it as you see fit. Choose **Single-Page App** and press **Enter**.

Use `http://localhost:8080/callback` for the Redirect URI and accept the default Logout Redirect URI of `http://localhost:8080`.

#### Server Configuration

Set the `issuer` and copy the `clientId` into `src/server.js`.

```javascript
const oktaJwtVerifier = new OktaJwtVerifier({
  clientId: '{yourClientId}',
  issuer: 'https://{yourOktaDomain}/oauth2/default'
})
```

#### Client Configuration

Set the `issuer` and copy the `clientId` into `src/router/index.js`.

```javascript
const oktaAuth = new OktaAuth({
  issuer: 'https://{yourOktaDomain}/oauth2/default',
  clientId: '{yourClientId}',
  redirectUri: window.location.origin + '/callback',
  scopes: ['openid', 'profile', 'email']
})
```

## Help

Please post any questions as comments on the [blog post](https://developer.okta.com/blog/2018/02/15/build-crud-app-vuejs-node), or visit our [Okta Developer Forums](https://devforum.okta.com/).
