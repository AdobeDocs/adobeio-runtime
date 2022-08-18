# Runtimes

Adobe I/O Runtime supports Node.js versions 16, 14, 12 and 10. Node v14 is the default image and the one used to create pre-warm cotainers. We encourage you to always update your actions to the latest version in order to take advantage of pre-warm containters feature.

The following npm modules are pre-installed (if your action uses any of these modules, you don&rsquo;t have to package them together with action code):

### Node.js v16.15.0

    "express": "4.18.1",
    "openwhisk": "3.21.6",
    "body-parser": "1.20.0",
    "redis": "4.1.0",
    "node-fetch": "3.2.4",
    "dnscache": "1.0.2",
    "prom-client": "13.2.0"

### Node.js v14.16.1

    "express": "4.17.1",
    "openwhisk": "3.21.6",
    "body-parser": "1.19.0",
    "cls-hooked": "4.2.2",
    "redis": "3.1.2",
    "node-fetch": "2.6.7",
    "dnscache": "1.0.2",
    "prom-client": "12.0.0"

### Node.js v12.22.1

    "express": "4.17.1",
    "openwhisk": "3.21.6",
    "body-parser": "1.19.0",
    "cls-hooked": "4.2.2",
    "redis": "3.0.2",
    "node-fetch": "2.6.7",
    "dnscache": "1.0.2",
    "prom-client": "12.0.0"

### Node.js v10.24.1

    "express": "4.16.4",
    "openwhisk": "3.21.6",
    "body-parser": "1.18.3",
    "cls-hooked": "4.2.2",
    "redis": "2.8.0",
    "request": "2.88.0",
    "request-promise": "4.2.2",
    "dnscache": "1.0.2",
    "prom-client": "12.0.0"

This is how you can specify explicitly this kind:
```
wsk action create actionName fromFile.js --kind nodejs:14 
```
or
```
wsk action create actionName fromFile.js --kind nodejs:12 
```
We will publish this image on GitHub and Docker Hub.
