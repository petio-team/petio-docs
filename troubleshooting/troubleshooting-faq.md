# FAQ

![](../.gitbook/assets/troubleshooting.gif)

## Docker

### Petio Crashes On Container Startup

#### Error Example \#1

```bash
| (node:8) UnhandledPromiseRejectionWarning: Error: getaddrinfo ENOTFOUND api.themoviedb.org
|     at GetAddrInfoReqWrap.onlookup [as oncomplete] (dns.js:67:26)
| (node:8) UnhandledPromiseRejectionWarning: Unhandled promise rejection. This error originated either by throwing inside of an async function without a catch block, or by rejecting a promise which was not handled with .catch(). To terminate the node process on unhandled promise rejection, use the CLI flag `--unhandled-rejections=strict` (see https://nodejs.org/api/cli.html#cli_unhandled_rejections_mode). (rejection id: 3)
| (node:8) UnhandledPromiseRejectionWarning: TypeError: Cannot read property 'results' of undefined
|     at trending (/app/api/tmdb/trending.js:28:30)
|     at processTicksAndRejections (internal/process/task_queues.js:93:5)
| (node:8) UnhandledPromiseRejectionWarning: Unhandled promise rejection. This error originated either by throwing inside of an async function without a catch block, or by rejecting a promise which was not handled with .catch(). To terminate the node process on unhandled promise rejection, use the CLI flag `--unhandled-rejections=strict` (see https://nodejs.org/api/cli.html#cli_unhandled_rejections_mode). (rejection id: 4)
| 2021-03-28 20:42:28 error: TypeError: Cannot set property 'timestamp' of null
petio exited with code 1
```

* Normally this is caused by the container trying to resolve an IPv6 address for `api.temoviedb.org`. To verify if this is the issue:
  * `docker exec  -it petio sh`
    * `nslookup api.themoviedb.org`
* To fix this issue, go back to when you first configured Docker and remember if you made some custom changes. This is not a Petio issue but rather an issue on your configuration.

## Linux

## MacOS

## unRAID

## Windows

