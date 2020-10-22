# Adobe I/O Runtime Developer Guide

This documentation provides an overview of Adobe I/O Runtime as well as guides, reference documentation, and tools to help you begin developing your own integrations. 

## Contents

[Quickstart guide:](quickstart.md) A one-page guide to help you quickly get started with Adobe I/O Runtime.

[Overview](overview.md)

* [What is Adobe I/O Runtime](overview/what_is_runtime.md)
* [Use Cases for Adobe I/O Runtime](overview/usecases.md)
* [How Adobe I/O Runtime Works](overview/howitworks.md)
* [Adobe I/O Runtime Entities](overview/entities.md)
* [Getting Access](overview/getting_access.md)

[Getting Started](getting_started.md)

* [Setting up Your Environment](getting-started/setup.md)
* [Deploying your First Adobe I/O Runtime Function](getting-started/deploy.md)
* [Retrieve Action Invocation Results](getting-started/activations.md)

[Guides](guides.md)

* [Creating Actions](guides/creating_actions.md): actions, web actions, invoking and managing, setting parameters
* [Asynchronous Calls](guides/asynchronous_calls.md): how to execute long running async (non-blocking) calls
* [Throughput Tuning](guides/throughput_tuning.md): how to maximize the number of action invocations
* [Security Guide](guides/security_general.md): discover potential security issues and how to address them
* [Securing Web Actions](guides/securing_web_actions.md): learn how to control the access to web actions
* [Creating REST APIs](guides/creating_rest_apis.md): learn to create REST APIs from web actions
* [Using Packages](guides/using_packages.md): Working with packages
* [Logging & Monitoring](guides/logging_monitoring.md): learn how to troubleshoot your actions
* [Debugging](guides/debugging.md): advanced debugging for Node.js actions
* [System Settings](guides/system_settings.md): see the system settings and constraints 
* [CI/CD Pipeline](guides/ci-cd_pipeline.md): understand the tools you have to create a CI/CD Pipeline

[Reference Documentation](reference.md)

* [aio CLI](reference/cli_use.md): how to use aio CLI
* [wsk CLI](reference/wsk_use.md): how to use wsk CLI
* [Environment Variables](reference/environment_variables.md): what environment variables do you have access to
* [Multiple Regions](reference/multiple_regions.md): where we run your actions
* [Pre-installed Packages](reference/prepackages.md): what packages are pre-installed 
* [Runtimes](reference/runtimes.md): details about the available runtimes
* [API Reference](reference/api_ref.md): I/O Management API
* [Triggers & Rules](reference/triggersrules.md): working with triggers and rules
* [Sequences & Compositions](reference/sequences_compositions.md): orchestrating actions
* [Packages](reference/packages.md): working with packages
* [Feeds](reference/feeds.md): working with feeds

[Tools](tools.md)

* [aio CLI](./tools/cli_install.md) - this tool helps you manage your namespaces and the authentication for the wsk CLI
* [wsk CLI](./tools/wsk_install.md) - this tool is the main interface for managing your actions/packages/rules/triggers and getting access to activation results/errors/logs
* [wskdeploy CLI](./tools/wskdeploy_install.md) - this tool helps you deploy multiple actions and packages

[Resources and Support](resources.md)

* [FAQ](resources/faq.md)
