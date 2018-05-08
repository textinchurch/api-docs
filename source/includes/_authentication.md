# Authentication

Authentication to the Text In Church API requires the use of [OAuth](https://en.wikipedia.org/wiki/OAuth) version 2.0.

Visit [textinchurch.com/developer/applications](https://textinchurch.com/developer/applications)
to create an OAuth application token.

> Example of sending the POST request using curl:

```
curl -X POST https://api.textinchurch.com/oauth/token \
     -F grant_type=authorization_code \
     -F code=1234567890 \
     -F client_id=2345678901 \
     -F client_secret=3456789012 \
     -F redirect_uri=https://mywebsite.com/auth/complete
```

> Sample response containing the access token:

```
{
  "access_token": "1234567890abcdef1234567890abcdef1234567890abcdef1234567890abcdef",
  "token_type": "bearer",
  "expires_in": 7200,
  "refresh_token": "1234567890abcdef1234567890abcdef1234567890abcdef1234567890abcdef",
  "scope": "people",
  "created_at": 1469553476
}
```

> Pass the access token in all subsequent API requests:

```
curl -H 'Authorization: Bearer 1234567890abcdef1234567890abcdef1234567890abcdef1234567890abcdef' https://api.textinchurch.com/people
```

Make sure your app conforms to the [OAuth 2.0](http://oauth.net/2/) specification. Generally, to authenticate a user,
follow these steps:

1.  Redirect the user's browser to `https://api.textinchurch.com/oauth/authorize?client_id=CLIENT_ID&redirect_uri=https://mywebsite.com/auth/complete&response_type=code&scope=people`
    (replace `CLIENT_ID` and `https://mywebsite.com/auth/complete` with your actual redirect URI).

    If you need different scope, replace `scope=people` appropriately (see "Scopes" section below).

2.  Text In Church will redirect the user's browser back to the given redirect URI with a `code` param.

3.  Send a POST request in the background to `https://api.textinchurch.com/oauth/token` with the following params:
    `{"grant_type": "authorization_code", "code": "CODE_FROM_STEP_2", "client_id": "CLIENT_ID", "client_secret": "CLIENT_SECRET", "redirect_uri": "https://mywebsite.com/auth/complete"}`
    (replace `CLIENT_ID`, `CLIENT_SECRET`, `CODE_FROM_STEP_2`, and the redirect URI appropriately).

4.  The response you get back will contain the access token and other information.

5.  Use the access token for all API requests by passing it in the `Authorization` header, using the `Bearer` authentication scheme.

OAuth access tokens expire after 2 hours from the time they are issued, but we also provide a
[refresh token](https://tools.ietf.org/html/rfc6749#section-1.5) you can use to get a new access token at any time,
even after the access token expires, without forcing the user to re-authorize.

We will honor refresh tokens for up to 1 year after the date its associated access token was issued.
This means that, if your app does not issue a refresh for 1 year, then your user will need to re-authorize.

### Scopes

Each Text In Church app is a distinct [OAuth scope](http://tools.ietf.org/html/rfc6749#section-3.3).


| App | Scope|
|-----|------|
| Groups | groups |
| People | people |

Authorization URL is [https://api.textinchurch.com/oauth/authorize](https://api.textinchurch.com/oauth/authorize)
Token URL is [https://api.textinchurch.com/oauth/token](https://api.textinchurch.com/oauth/token)
When authorizing, you can request scopes using the `scope` parameter. The value should be a space-separated list of scopes.
The value for `response_type` should be `code`
