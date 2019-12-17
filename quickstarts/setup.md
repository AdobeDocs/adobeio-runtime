# Setting up Your Environment

Before you can create and run actions, you have to install and configure a couple of tools on your machine. Please note that for some of the steps (creating integrations in I/O Console) you need to have System Administrator or Developer Role permissions. If you don&rsquo;t have those, you need either to be provisioned with these permissions or someone from your team has to share the credentials.

## Step 1: Install aio CLI and wsk CLI

You need `npm` installed in order to install `aio` (make sure you have the latest versions of Node and npm installed):

`npm install -g @adobe/aio-cli`

For the `wsk` CLI, download the executable from the [OpenWhisk GitHub repository](https://github.com/apache/incubator-openwhisk-cli/releases). Choose the version that matches your operating system and download the compressed archive.

Extract the executable from the compressed archive and place it in a folder of your choice.

Add the folder into which you placed the executable to your `$PATH` environment variable. This enables you to call the CLI from anywhere.

Try to run these commands to check that `aio` and `wsk` were properly installed:

`wsk -h`

and:

`aio -h`

### Configuring the wsk CLI with a .wskprops file

If you have a `.wskprops` file, then you can use it to configure the `wsk` CLI, so you'll be creating actions in the namespace that is defined in that file.

For Mac, you just need to copy the `.wskprops` in the user home folder.

For Windows, you'll place the `.wskprops` in `C:\Users\<user>`.

### Configuring aio CLI to use your .wskprops file

The aio CLI will pickup credentials from the exact same path as the wsk CLI ( above )

Additionally, the aio CLI allows the use .env files, so if you have multiple namespaces you can have a different set of credentials associated with each project/directory.  aio CLI always looks for a .env file in the current working directory before looking to the default location of .wskprops

Here are the keys you need to add to the .env file:
```
AIO_RUNTIME_APIHOST=https://adobeioruntime.net
AIO_RUNTIME_AUTH=<auth-string-value>
AIO_RUNTIME_NAMESPACE=<namespace-value>
```

> Note: .env files are hidden by default, so you may not see them. Also, you should add them to .gitignore and never commit them to source control.


## Step 2: Testing the CLI is setup correctly

Once you&rsquo;ve configured the CLI, you should test it:

`wsk list`

`aio runtime list`

If successful, you should see a list of the entities defined in your namespace.

You&rsquo;re ready to [deploy your first function](deploy.md).
