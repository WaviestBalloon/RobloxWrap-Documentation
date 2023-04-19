# Exception documentation

## Client specified errors

Any errors that are related to the Client. It is recommended to take a look at the ["Debugging potential errors"](https://robloxwrap.fur.dev/guide/introduction.html#debugging-potential-errors) in the Introduction for debugging these errors.

### ClientError

For errors that relate to the Client class, for example, Client.login or internal issues.

### TokenError

Generic Token error, for example, CSRF-Token generation errors.

### TokenValidationError

For errors that relate to token validation, this happens when a `.ROBLOSECURITY` fails verification.

## API specified errors

Any errors that are related to the handling of Roblox API endpoints.

### EndpointError

A generic error that is thrown when handling an endpoint encounters a error when sending requests, for example, `getUserInfo` might error when the UserID is invalid.

```javascript
client.getUserInfo(54279857428427538);
```
```javascript
EndpointError: User does not exist
```

### WebsocketEndpointError

For errors that relate to websockets, sometimes the socket connection fails to contact `realtime.roblox.com`, the implementation is very janky but works.

### DatatypeValidationError

For errors that relate to datatype validation, for example, `getUserInfo` will throw this error if the UserID is not a number.

```javascript
client.getUserInfo("onetwofive");
```
```javascript
DatatypeValidationError: Invalid userId, the userId is not a number
```

