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

The `aio` CLI will pickup credentials from the exact same path as the wsk CLI ( above )

Additionally, the `aio` CLI allows the use .env files, so if you have multiple namespaces you can have a different set of credentials associated with each project/directory.  `aio` CLI always looks for a .env file in the current working directory before looking to the default location of .wskprops

Here are the keys you need to add to the .env file:
```
AIO_RUNTIME_APIHOST=https://adobeioruntime.net
AIO_RUNTIME_AUTH=<auth-string-value>
AIO_RUNTIME_NAMESPACE=<namespace-value>
```

> Note: .env files are hidden by default, so you may not see them. Also, you should add them to .gitignore and never commit them to source control.

## Step 2: Testing the CLI is setup correctly

Once you've configured the CLI, you should test it:

`wsk list`

`aio runtime list`

If successful, you should see a list of the entities defined in your namespace.

You&rsquo;re ready to [deploy your first function](deploy.md).

## Optional Step: Generating your .wskprops file from I/O Console

It is possible to use the `aio` CLI to generate your .wskprops file. This only applies if you have been onboarded on Runtime through Console. In other words, Runtime must have been enabled for your integration in I/O Console directly.

### Enabling Runtime from I/O Console

- Create or Edit the integration that you want to use in Runtime
- Add the I/O Management API to this integration
- Make sure that you enable Runtime for that integration in I/O Console directly

Once this is done, you will need to configure the `aio` CLI according to this integration.

### Configuring aio CLI

Create a `config.json` file on your computer and navigate to the integration Overview page. From this page, copy the `client_id` and `client_secret` values to the config file; if you navigate to the JWT tab in Console, you'll get the value for the `jwt_payload`.

```
//config.json 
{
  "client_id": "value from your CLI integration (String)",
  "client_secret": "value from your CLI integration (String)",
  "jwt_payload": { value from your CLI integration (JSON Object Literal) },
  "token_exchange_url": "https://ims-na1.adobelogin.com/ims/exchange/jwt",
  "console_get_orgs_url":"https://api.adobe.io/console/organizations",
  "console_get_namespaces_url":"https://api.adobe.io/runtime/admin/namespaces/"
}
```

The last bit you need to have at hand is the private certificate you've used to create the integration; you need the private key, not the public one. Now, you are ready to configure the `aio` CLI.

First, configure the credentials:

`aio config set jwt-auth PATH_TO_CONFIG_JSON_FILE --file --json`

Then, configure the private certificate:

`aio config set jwt-auth.jwt_private_key PATH_TO_PRIVATE_KEY_FILE`

Note that this just stores the path to your private key in the CLI configuration.

### Testing your AIO CLI configuration

To test that `aio` CLI can actually authenticate against Adobe I/O, run this command to list all the integrations that your organization has:

`aio console list-integrations`

This command will list all available integrations in your org. Pipe the command to [`less`](https://en.wikipedia.org/wiki/Less_(Unix)) or [`more`](https://en.wikipedia.org/wiki/More_(command)) to page the results.

You can also use [`grep`](https://en.wikipedia.org/wiki/Grep) to filter the results.

Sample output:

```
Namespace      Name                      API Key        Status
NUMBER_NUMBER  Integration Name 1        HEX_KEY        ENABLED
NUMBER_NUMBER  Integration Name 2        HEX_KEY        DISABLED
NUMBER_NUMBER  Integration Name 3        HEX_KEY        ENABLED (currently selected)
NUMBER_NUMBER  Integration Name 4        HEX_KEY        ENABLED
```

Note that the status of an integration can be `ENABLED` or `DISABLED` and one integration in the list will be flagged as being `currently selected`.

### Selecting Console integration & Runtime namespace

Now you can use the `aio` CLI to select the namespace that you enabled from Console and use it for deploying actions. There is a 1:1 relationship between an integration and a namespace, so if you select your integration from the list above, you will also select the corresponding namespace. 

You can't manage multiple namespaces at the same time. You can only have just one namespace active always, and all the actions you perform are against the active namespace.

To list the available integrations, run:

`aio console list-integrations`

Identify your integration in the list and run the command below and pass as the argument the <NUMBER_NUMBER> you see listed when running `aio console list-integrations`:

`aio console select-integration <NUMBER_NUMBER>`

This command will generate the `.wskprops` file in your user directory (or overwrite the file if it already exists) for accessing that given namespace. Now, you can use `aio` CLI or `wsk` CLI to manage this namespace: create/invoke actions and so forth.
