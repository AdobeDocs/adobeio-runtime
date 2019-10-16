# Setting up Your Environment

Before you can create and run actions, you have to install and configure a couple of tools on your machine. 

## Step 1: Install aio CLI

You need `npm` installed in order to install `aio` (make sure you have the latest versions of Node and npm installed):

`npm install -g @adobe/aio-cli`

Try this command to check that `aio` was properly installed:

`aio -h`

## Step 2: Install aio runtime plugin

`aio plugins add @adobe/aio-cli-plugin-runtime`

## Step 3: Get a wskprops file

[TODO ... elaborate how]
... generate the `.wskprops` file in your user directory (or overwrite the file if it already exists) for accessing that given namespace. Now, you can use the `aio` CLI to manage this namespace: create/invoke actions and so forth.

## Step 4: Test wsk CLI

Once you&rsquo;ve configured the CLI, you should test it:

`aio runtime list`

If successful, you should see a list of the entities defined in your namespace.

You&rsquo;re ready to [deploy your first function](deploy.md).
