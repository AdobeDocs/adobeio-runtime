# Retrieve Action Invocation Results

Every time an action is executed, an activation record is created. The activation record contains information that helps you understand what happened: activation ID (the unique indentifier), namespace and action name, logs (if any), response (a dictionary that contains the status, success, and result).

## Activations TTL

The activation TTL (Time To Live) is seven days. This is a system setting, not a user setting (it can't be changed by developers).

Thus, if you don't see any activations or not seeing an activation you know that has happened, it could be that they happend more than 7 days ago.

## Example

Assuming that you&rsquo;ve invoked an action called `hello`, this is how you retrieve the latest activations:

`wsk activation list`

The result will be a list of activation IDs (if any) and the action invoked for each:

```
e9932762894d4ccf932762894d6ccff4 hello            
c76dbe66e9b04ad5adbe66e9b06ad541 hello            
[]...]
```

You can retrieve the whole activation record by running `wsk activation get <activation id>`:

```
wsk activation get e9932762894d4ccf932762894d6ccff4
ok: got activation e9932762894d4ccf932762894d6ccff4
{
    "namespace": "your-namespace",
    "name": "hello",
    "version": "0.0.20",
    "subject": "your-namespace",
    "activationId": "e9932762894d4ccf932762894d6ccff4",
    "start": 1542232412321,
    "end": 1542232412366,
    "duration": 45,
    "response": {
        "status": "success",
        "statusCode": 0,
        "success": true,
        "result": {
            "body": {
                "payload": {
                    "message": "hello world!"
                }
            },
            "statusCode": 200
        }
    },
    "logs": [],
    "annotations": [
        {
            "key": "path",
            "value": "your-namespace/hello"
        },
        {
            "key": "waitTime",
            "value": 23
        },
        {
            "key": "kind",
            "value": "nodejs:10-fat"
        },
        {
            "key": "limits",
            "value": {
                "logs": 10,
                "memory": 256,
                "timeout": 60000
            }
        },
        {
            "key": "initTime",
            "value": 40
        }
    ],
    "publish": false
}
```

Or you can extract a specific part from the activation record:

```
// just the result
wsk activation result <activation ID>

// just the logs
wsk activation logs <activation ID>
```

## Blocking successful activations

Status of the blocking successful activations can't be retrieved at a later time. 
As a consequence, the following wsk commands will partially work as expected: 
- `wsk activation logs <activation ID>` will still display the logs for the activations.
- `wsk activation list` won't display the blocking successful activations. 
- `wsk activation get <activation ID>` won't return the activation result. 

You can still make blocking successful web activations retrievable at a later time, by setting in the request the extra logging header to `on`: 
```
X-OW-EXTRA-LOGGING: on
``` 

## Retrieving Activations for Non-blocking Calls

When you execute a non-blocking action (async action), the action returns immediately the activation ID. If you query for the result or logs before the action finished the execution you get an error:
```
wsk activation get 1d24121f91384740a4121f91389740f0
error: Unable to get activation '1d24121f91384740a4121f91389740f0': The requested resource does not exist. (code myM2aaCufgIcnjnrbNIHztNmhL2HvFia)


wsk activation logs c8c4f354c1824f2c84f354c182ef2cdb
error: Unable to get logs for activation 'c8c4f354c1824f2c84f354c182ef2cdb': The requested resource does not exist. (code nCPo4KRbYmvOTcwPQVfDJdrwtJpv1c3d)
```

This should give you enough tools to debug your first actions. If you want to read more, take a look at the [Logging and Monitoring](../guides/logging_monitoring.md 'Logging and Monitoring') page.
