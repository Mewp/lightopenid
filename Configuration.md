LightOpenID is configured by setting certain variables on an object, for example:

```
$openid = new LightOpenID;
$openid->identity = 'openid.example.com'
```

The following options are avaiable:

| **name**    | **description** |
|:------------|:----------------|
| identity    | Sets (or gets) the identity supplied by an user. Set it before calling authUrl(), and get after validate(). |
| returnUrl   | Users will be redirected to this url after they complete authentication with their provider. Default: current url. |
| realm       | The realm user is signing into. Providers usually say "You are sgning into $realm". Must be in the same domain as returnUrl. Usually, this should be the host part of your site's url. And that's the default. |
| required and optional | Attempts to fetch more information about an user. See [GettingMoreInformation](http://code.google.com/p/lightopenid/wiki/GettingMoreInformation). |
| verify\_peer | When using https, attempts to verify peer's certificate. See [CURLOPT\_SSL\_VERIFYPEER](http://pl2.php.net/manual/en/function.curl-setopt.php). |
| cainfo and capath | when verify\_peer is true, sets the CA info file and directory, respecively. See [CURLOPT\_SSL\_CAINFO](http://pl2.php.net/manual/en/function.curl-setopt.php) and [CURLOPT\_SSL\_CAPATH](http://pl2.php.net/manual/en/function.curl-setopt.php). |