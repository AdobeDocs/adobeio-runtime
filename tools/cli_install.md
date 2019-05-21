# Setting up the `aio` CLI

The `aio` CLI helps you to manage the `.wskprops` file as you use different namespaces. 

You need `npm` installed in order to install it. Before you start, make sure you have the latest version of Node and npm installed.

```
npm install -g @adobe/aio-cli
```

After this, you can run help to see all the commands and verify that you are all set:

```
aio -h
```

If you want to update to the latest version, run:
```
aio plugins:update
```
## Reseting the auth credentials for a namespace

 If you want to change the credentials used to manage a namespace (the hash stored in the `.wskprops` file), you can run this command:

```
aio console:reset-integration INTEGRATION_ID
``

You can retrieve the 'INTEGRATION_ID` from I/O Console or by listing all the integrations and look for the one you need (`aio console:list-integrations`) - the second number on each row represents is the `INTEGRATION_ID`.

For more information about the `aio` CLI check the [package home page](https://www.npmjs.com/package/@adobe/aio-cli).
