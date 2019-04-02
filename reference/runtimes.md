# Runtimes

Adobe I/O Runtime supports Node.js version 10. The following npm modules are pre-installed (if your action uses any of these modules, you don&rsquo;t have to package them together with action code):
1. `express` version 4.16.4
2. `openwhisk` version 3.18.0
3. `body-parser` version 1.18.3
4. `cls-hooked` version 4.2.2
5. `request` version 2.88.0
6. `request-promise` version 4.2.2

This is how you can specify explicitly this kind:
```
wsk action create actionName fromFile.js --kind nodejs:10 
```

We will publish this image on GitHub and Docker Hub.
