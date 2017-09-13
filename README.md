# Google Wifi API

**Discovered API-endpoints for the Google Wifi Router and OnHub**

The default submask/IP for the Google Wifi Router is 192.168.86.1, using a Google (TP-LINK) OnHub you should also be able to reach the endpoints via http://on.here/.

Collecting this information to maybe build a nifty macOS-app further down the road.

### Discovered API-endpoints:

`http://192.168.86.1/api/v1/welcome-mat`  
OnHub-specific

`http://192.168.86.1/api/v1/status`  
Displays useful status information for the router

`http://192.168.86.1/api/v1/connected-devices`  
Seems to require some kind of authentication?
**Update:** If you set the `Host` header's value to `localhost` or `onehub.here` you'll get a 200 response with a response with one field, `hueBridges`.

Example use using [httpie](https://httpie.org):
```
$ http --print hbHB http://192.168.86.1/api/v1/connected-devices 'Host:onhub.here'
GET /api/v1/connected-devices HTTP/1.1
Accept: */*
Accept-Encoding: gzip, deflate
Connection: keep-alive
Host: onhub.here
User-Agent: HTTPie/0.9.9



HTTP/1.1 200 OK
Connection: Keep-Alive
Content-Length: 27
Content-Type: application/json; charset=utf-8
Date: Wed, 13 Sep 2017 21:47:46 GMT

{
    "_hueBridges": []
}
```

`http://192.168.86.1/api/v1/get-endorsement-information`  
Just gives the message "device is registered"

`http://192.168.86.1/api/v1/get-attestation-information`  
Just gives the message "device is registered"

`http://192.168.86.1/api/v1/diagnostic-report`  
Generates a rather large (> 1.1MB) file with some really interesting diagnostics info together with some kind of encoded data-dump.
