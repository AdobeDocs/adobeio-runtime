# Setting up Your Environment

> Note: these instructions assume that you have already aquired a namespace and have a valid namespace/authorization stored at ~/.wskprops
> If you have not already, please [Request a Trial](../overview/request_a_trial.md)

Before you can create and run actions, you have to install and configure a couple of tools on your machine. 

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

## Step 2: Test aio CLI and/or wsk CLI

Once you&rsquo;ve configured the CLI, you should test it:

`aio runtime list`  

and: 

`wsk list`

If successful, you should see a list of the entities defined in your namespace.

To see a list of all the available commands, both CLIs provide --help flags

`aio runtime --help`

`aio runtime action --help`

and:

`wsk --help`

`wsk action --help`

You&rsquo;re ready to [deploy your first function](deploy.md).