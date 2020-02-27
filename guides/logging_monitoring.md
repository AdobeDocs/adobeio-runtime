# Logging and Monitoring

The `wsk` CLI offers a number of tools you can use to debug your actions while running them on Adobe I/O Runtime.

You can retrieve the latest activations in a namespace by running:
```
wsk activation list
```
Having an activation ID, you can retrieve the actication result running:
```
wsk activation get <activation ID>
```
If you send data to logs from your actions (using `console.log()` in your code), you&rsquo;ll get this information as part of the activation record, inside the `logs` field. The shortcut command to get the logs is:
```
wsk activation logs <activation ID>
//output sample
2018-11-14T22:23:00.002Z       stdout: 1542234180001: param = John Doe
```

## 3rd-Party Tools

I/O Runtime doesn’t offer a configuration to send activations and logs to an external system, something like Splunk, Datadog or New Relic. This is something we are considering to offer in the future. 

Although there is no out-of-the-box integration, there are still ways you can push data from I/O Runtime to an external tool in order to monitor and debug your actions. 

One tool that made it easy to do this is [Epsagon](https://epsagon.com/?utm_source=adobe.io&utm_medium=referral&utm_campaign=adobe_io_docs). Epsagon built an integration for OpenWhisk based systems (I/O Runtime is built on top of the open source project OpenWhisk) that makes super easy to see your activations, errors, latency information and logs in their system. Check this [guide](https://docs.epsagon.com/docs/openwhisk?utm_source=adobe.io&utm_medium=referral&utm_campaign=adobe_io_docs) or this [video presentation](https://www.youtube.com/watch?v=4iprbivqrxQ&t=1517s) if you want to find more. 

## Debugging Locally

Check this [page](debugging.md) if you want to learn how to debug your actions locally.