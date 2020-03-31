# Keycloak.js

[Keycloak.js Library](https://github.com/keycloak/keycloak-js-bower/blob/master/dist/keycloak.js)

## Keycloak(config)

- constructor of the Keycloak "class"
- all further functions are included
- functions without `kc.` are probably not callable from outside
- properties:
  - `kc = this;`: kc is a reference to the current Keycloak object
  - `kc.token`: bearer token
  - `callbackStorage`: local storage (default) or cookie storage

## kc.init(initOptions)

- adapter is loaded (`'default', 'cordova', 'cordova-native'`)
- initOptions are set
- no request is sent

#### onLoad()

- contained methods:
  - `doLogin(prompt)`: run `kc.login(options)` -> TODO: request?
  - `checkSsoSilently()`: handle silent sso
- if `initOptions.onLoad` is `check-sso` or `login-required` then `doLogin()` is executed

#### processInit()

- previous functions are executed

## kc.login(options)

- führt nur `adapter.login(options)` aus

## kc.logout(options)

- führt nur `adapter.logout(options)` aus

## TODO: generateRandomData(len)

## generateCodeVerifier(len)

- führt nur `generateRandomString()` aus

## TODO: generateRandomString(len, alphabet)

## TODO: generatePkceChallenge(pkceMethod, codeVerifier)

## kc.createLoginUrl(options)

- creates and returns url for path `'/auth'` if `options.action !== 'register'`
- TODO: where is this url used?

## TODO: kc.createLogoutUrl(options)

## TODO: kc.register(options)

## TODO: kc.createRegisterUrl(options)

## TODO: kc.createAccountUrl(options)

## TODO: kc.accountManagement()

## TODO: kc.hasRealmRole(role)

## TODO: kc.hasResourceRole(role, resource)

## kc.loadUserProfile()

- sends request to `'/account'`
- runs on success:

```js
kc.profile = JSON.parse(req.responseText);
promise.setSuccess(kc.profile);
```

## kc.loadUserInfo()

- sends request to `kc.endpoints.userinfo()`
- resolves to `'/userinfo'` if OIDC server is **not** used
- runs on success:

```js
kc.userInfo = JSON.parse(req.responseText);
promise.setSuccess(kc.userInfo);
```

## TODO: kc.isTokenExpired()

## kc.updateToken(minValidity = 5)

- `kc.refreshToken` is necessary. Otherwise an error will occur.
- `checkLoginIframe()` is executed if `loginIframe.enable === true`
- then sends request to `kc.endpoints.token()`
- resolves to `'/token'` if OIDC server is **not** used
- runs on success:

```js
setToken(
  tokenResponse['access_token'],
  tokenResponse['refresh_token'],
  tokenResponse['id_token'],
  timeLocal
);
kc.onAuthRefreshSuccess && kc.onAuthRefreshSuccess();
```

## TODO: kc.clearToken()

## TODO: getRealmUrl()

## TODO: getOrigin()

## TODO: processCallback(oauth, promise)

- enthaltene Methode: `authSuccess(accessToken, refreshToken, idToken, fulfillPromise)`

## TODO: loadConfig(url)

- enthält weitere Methoden

## TODO: fileLoaded(xhr)

## TODO: setToken(token, refreshToken, idToken, timeLocal)

## TODO: decodeToken(str)

## TODO: createUUID()

## TODO: parseCallback(url)

## TODO: parseCallbackUrl(url)

## TODO: parseCallbackParams(paramsString, supportedParams)

## TODO: createPromise(internal)

## TODO: createNativePromise()

## TODO: createLegacyPromise()

## TODO: setupCheckLoginIframe()

## TODO: scheduleCheckIframe()

## TODO: checkLoginIframe()

## TODO: loadAdapter(type)

- enthält weitere Methoden

## LocalStorage()

- constructor of the LocalStorage "class"
- used as default
- current state is saved to local storage:

```js
var key = 'kc-callback-' + state.state;
state.expires = new Date().getTime() + 60 * 60 * 1000;
localStorage.setItem(key, JSON.stringify(state));
```

## CookieStorage()

- constructor of the CookieStorage "class"
- current state is saved as a cookie:

```js
setCookie(
  'kc-callback-' + state.state,
  JSON.stringify(state),
  cookieExpiration(60)
);
```

## createCallbackStorage()

- try to use **local storage**, use **cookie storage** if local storage fails

## TODO: createLogger(fn)
