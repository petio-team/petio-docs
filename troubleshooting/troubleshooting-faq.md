# FAQ

![](../.gitbook/assets/troubleshooting.gif)

## Petio Crashes On Container Startup

### Docker

Error example:

```bash
petio          | 2021-03-28 20:42:28 info: LOGIN: New login attempted
petio          | 2021-03-28 20:42:28 info: LOGIN: Request IP: ::ffff:127.0.0.1
petio          | 2021-03-28 20:42:28 info: LOGIN: No JWT: <REDACTED_EMAIL>
petio          | 2021-03-28 20:42:28 info: LOGIN: Request User: <REDACTED_EMAIL>
petio          | 2021-03-28 20:42:28 info: History returned from source
petio          | 2021-03-28 20:42:28 info: History returned from source
petio          | (node:8) UnhandledPromiseRejectionWarning: Error: getaddrinfo ENOTFOUND api.themoviedb.org
petio          |     at GetAddrInfoReqWrap.onlookup [as oncomplete] (dns.js:67:26)
petio          | (node:8) UnhandledPromiseRejectionWarning: Unhandled promise rejection. This error originated either by throwing inside of an async function without a catch block, or by rejecting a promise which was not handled with .catch(). To terminate the node process on unhandled promise rejection, use the CLI flag `--unhandled-rejections=strict` (see https://nodejs.org/api/cli.html#cli_unhandled_rejections_mode). (rejection id: 3)
petio          | (node:8) UnhandledPromiseRejectionWarning: TypeError: Cannot read property 'results' of undefined
petio          |     at trending (/app/api/tmdb/trending.js:28:30)
petio          |     at processTicksAndRejections (internal/process/task_queues.js:93:5)
petio          | (node:8) UnhandledPromiseRejectionWarning: Unhandled promise rejection. This error originated either by throwing inside of an async function without a catch block, or by rejecting a promise which was not handled with .catch(). To terminate the node process on unhandled promise rejection, use the CLI flag `--unhandled-rejections=strict` (see https://nodejs.org/api/cli.html#cli_unhandled_rejections_mode). (rejection id: 4)
petio          | 2021-03-28 20:42:28 error: TypeError: Cannot set property 'timestamp' of null
petio exited with code 1
```

* Normally this is caused by the container trying to resolve an IPv6 address for `api.temoviedb.org`. To verify if this is the issue:
  * `docker exec  -it petio sh`
    * `nslookup api.themoviedb.org`

#### FIX:

* Go back to when you first configured Docker and remember if you made some custom changes. This is **not** a Petio issue but rather an issue on your configuration.

