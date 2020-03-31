# Keycloak.js

[Keycloak.js Library](https://github.com/keycloak/keycloak-js-bower/blob/master/dist/keycloak.js)

## TODO: function Keycloak(config)

- Konstruktor für die Keycloak-"Klasse"
- enthält alle weiteren Funktionen
- `var kc = this;`: kc ist eine Referenz auf das aktuelle Keycloak-Objekt
- Funktionen ohne `kc.` sind von außen wohl nicht aufrufbar

## FIXME: kc.init(initOptions)

- initialise function
- TODO: welche Requests werden gesendet?
- enthaltene Methoden:

  - `onLoad()`: TODO:
  - `checkSsoSilently()`: TODO:
  - `processInit()`: TODO:

- Properties:
  - `kc.token`: bearer token

## kc.login(options)

- führt nur `adapter.login(options)` aus

## kc.logout(options)

- führt nur `adapter.logout(options)` aus

## TODO: generateRandomData(len)

## generateCodeVerifier(len)

- führt nur `generateRandomString()` aus

## TODO: generateRandomString(len, alphabet)

## TODO: generatePkceChallenge(pkceMethod, codeVerifier)

## TODO: kc.createLoginUrl(options)

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

## TODO: LocalStorage()

- Konstruktor für LocalStorage-"Klasse"

## TODO: CookieStorage()

- Konstruktor für CookieStorage-"Klasse"

## TODO: createCallbackStorage()

## TODO: createLogger(fn)
