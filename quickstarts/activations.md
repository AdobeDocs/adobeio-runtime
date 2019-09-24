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

This should give you enough tools to debug your first actions. If you want to read more, take a look at the [Logging and Monitoring](../guides/logging_monitoring.md 'Logging and Monitoring') page.