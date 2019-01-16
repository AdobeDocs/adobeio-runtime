# Adobe I/O Runtime API Reference

## On this page
- [GET /runtime/admin/namespaces/{orgId}/{intId}](getruntimeadminnamespacesorgidintid)
- [POST /runtime/admin/namespaces/{orgId}/{intId}](postruntimeadminnamespacesorgidintid)
- [DELETE /runtime/admin/namespaces/{orgId}/{intId}](deleteruntimeadminnamespacesorgidintid)
- [GET /runtime/namespaces/{orgId}/{intId}/actions](getruntimenamespacesorgidintidactions)
- [POST /runtime/namespaces/{orgId}/{intId}/actions](postruntimenamespacesorgidintidactions)
- [GET /runtime/namespaces/{orgId}/{intId}/actions/{name}](getruntimenamespacesorgidintidactionsname)
- [POST /runtime/namespaces/{orgId}/{intId}/actions/{name}](postruntimenamespacesorgidintidactionsname)
- [PUT /runtime/namespaces/{orgId}/{intId}/actions/{name}](putruntimenamespacesorgidintidactionsname)
- [DELETE /runtime/namespaces/{orgId}/{intId}/actions/{name}](deleteruntimenamespacesorgidintidactionsname)
- [GET /runtime/system/actions](getruntimesystemactions)
- [POST /runtime/namespaces/{orgId}/{intId}/handleEventRegistration](postruntimenamespacesorgidintidhandleeventregistration)
- [DELETE /runtime/namespaces/{orgId}/{intId}/handleEventDeletion/{clientId}/{registrationId}](deleteruntimenamespacesorgidintidhandleeventdeletionclientidregistrationid)
- [PUT /runtime/namespaces/{orgId}/{intId}/handleEventUpdate/{clientId}/{registrationId}](putruntimenamespacesorgidintidhandleeventupdateclientidregistrationid)
- [POST /runtime/namespaces/{orgId}/{intId}/handleEventStatus/{clientId}/{registrationId}/{status}](postruntimenamespacesorgidintidhandleeventstatusclientidregistrationidstatus)

## API endpoints

Adobe I/O Runtime supports the following API endpoints for interacting programmatically with the service. 

**Notes:**
1. Unless otherwise noted, all parameters are required. 
2. For all the API calls on this page, the base URL is:  
`https://api.adobe.io/`

### GET /runtime/admin/namespaces/{orgId}/{intId}
Returns the details of the namespace associated with the specified organization and integration.

#### _Parameters:_
| Name | Description |
|---|---|
| `orgId` (`string`: _path_) | Organization ID |
| `intId` (`string`: _path_) | Integration ID |
| `Authorization` (`string`: _header_) | Authorization token in format: `Bearer {token}` |
| `X-Api-Key` (`string`: _header_) | Api key |

#### _Responses:_
Response content type: `application/json`
<table>
    <thead>
        <tr>
            <th>Code</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td style="vertical-align:top">200</td>
            <td><em>Successful operation</em><br />Example value:
<pre><code>{
    "name": "string",
    "auth": "string"
}</code></pre>
Model:
<pre><code>NamespaceDTO {
<em>description: Namespace Details</em>
    name    string
            Namespace name
    auth    string
            Auth associated with Namespace
}</code></pre>
            </td>
        </tr>
    </tbody>
</table>

### POST /runtime/admin/namespaces/{orgId}/{intId}
Creates a new namespace and returns the details of the newly created namespace. If namespace already exists it returns the details of the namespace.

#### _Parameters:_
| Name | Description |
|---|---|
| `orgId` (`string`: _path_) | Organization ID |
| `intId` (`string`: _path_) | Integration ID |
| `Authorization` (`string`: _header_) | Authorization token in format: `Bearer {token}` |
| `X-Api-Key` (`string`: _header_) | Api key |

#### _Responses:_
Response content type: `application/json`
<table>
    <thead>
        <tr>
            <th>Code</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td style="vertical-align:top">200</td>
            <td><em>Successful operation</em> <br />Example value:
<pre><code>{
"name": "string",
"auth": "string"
}</code></pre>
Model:
<pre><code>NamespaceDTO {
description: Namespace Details
    name    string
            Namespace name
    auth    string
            Auth associated with Namespace
}</code></pre>
            </td>
        </tr>
    </tbody>
</table>

### DELETE /runtime/admin/namespaces/{orgId}/{intId}
Deletes the namespace associated with the specified organization and integration.

#### _Parameters:_
| Name | Description |
|---|---|
| `orgId` (`string`: _path_) | Organization ID |
| `intId` (`string`: _path_) | Integration ID |
| `Authorization` (`string`: _header_) | Authorization token in format: `Bearer {token}` |
| `X-Api-Key` (`string`: _header_) | Api key |

#### _Responses:_
Response content type: `application/json`
| Code | Description |
|---|---|
| _default_ | Successful operation |

### GET /runtime/namespaces/{orgId}/{intId}/actions
Returns the list of actions associated with the specified organization and integration.

#### _Parameters:_
| Name | Description |
|---|---|
| `orgId` (`string`: _path_) | Organization ID |
| `intId` (`string`: _path_) | Integration ID |
| `Authorization` (`string`: _header_) | Authorization token in format: `Bearer {token}` |
| `X-Api-Key` (`string`: _header_) | Api key |

#### _Responses:_
Response content type: `application/json`
<table>
    <thead>
        <tr>
            <th>Code</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td style="vertical-align:top">200</td>
            <td><em>Successful operation</em> <br />Example value:
<pre><code>[
  {
    "name": "string",
    "code": "string",
    "namespace": "string",
    "version": "string",
    "params": [
      {
        "key": "string",
        "value": {}
      }
    ],
    "annotations": [
      {
        "key": "string",
        "value": {}
      }
    ],
    "limits": {
      "timeout": "string",
      "memory": "string",
      "logs": "string"
    },
    "exec": {
      "kind": "string",
      "binary": false,
      "components": [
        "string"
      ]
    },
    "url": "string"
  }
]</code></pre>
Model: 
<pre><code>[ActionDTO {
<em>description: OpenWhisk Action</em>
name        string
            Action name
code        string
            Action code
namespace   string
            Action namespace
version     string
            Action version
params      [Action params
            KeyValuePairDTO {
            <em>description: OpenWhisk Action param</em>
            key     string
                    Param Name
            value   {
                        <em>description: Param value</em>
                    }
            }]
annotations [Action annotations
            KeyValuePairDTO {
            <em>description: OpenWhisk Action param</em>
            key     string
                    Param Name
            value   {
                        <em>description: Param value</em>
                    }
            }]
limits      LimitsDTO {
            <em>description: OpenWhisk Action Limits</em>
            timeout     string
                        Action timeout
            memory      string
                        Action memory limit
            logs        string
                        Action logs
            }
exec        ExecDTO {
            <em>description: OpenWhisk Action exec details</em>
            kind    string
            Action kind
            binary  boolean
                    <em>default: false</em>
                    Is action binary
            components  [
                        Action components in case of sequence
                        string]
            }
url         string
            Action url
}]
</code></pre>
            </td>
        </tr>
    </tbody>
</table>

### POST /runtime/namespaces/{orgId}/{intId}/actions
Creates a new action.

#### _Parameters:_
<table>
    <thead>
        <tr>
            <th>Name</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
        <td><code>orgId</code> (<code>string</code>: <em>path</em>)</td>
        <td>Organization ID</td>
        </tr>
        <tr>
        <td><code>intId</code> (<code>string</code>: <em>path</em>)</td>
        <td>Integration ID</td>
        </tr>
        <tr>
        <td style="vertical-align:top"><code>body</code> (<em>body</em>)</td>
        <td>Action form. <br> Example value: 
<pre><code>{
  "name": "string",
  "code": "string",
  "namespace": "string",
  "version": "string",
  "params": [
    {
      "key": "string",
      "value": {}
    }
  ],
  "annotations": [
    {
      "key": "string",
      "value": {}
    }
  ],
  "limits": {
    "timeout": "string",
    "memory": "string",
    "logs": "string"
  },
  "exec": {
    "kind": "string",
    "binary": false,
    "components": [
      "string"
    ]
  },
  "url": "string"
}</code></pre>Parameter content type: <code>application/json</code>
Model: 
<pre><code>[ActionDTO {
<em>description: OpenWhisk Action</em>

name        string
            Action name
code        string
            Action code
namespace   string
            Action namespace
version     string
            Action version
params      [Action params
            KeyValuePairDTO {
            <em>description: OpenWhisk Action param</em>
            
            key     string
                    Param Name

            value   {
                        <em>description: Param value</em>
                    }
            }]

annotations [Action annotations
            KeyValuePairDTO {
            <em>description: OpenWhisk Action param</em>
            
            key     string
                    Param Name

            value   {
                        <em>description: Param value</em>
                    }
            }]

limits      LimitsDTO {
            <em>description: OpenWhisk Action Limits</em>
            
            timeout     string
                        Action timeout
            
            memory      string
                        Action memory limit

            logs        string
                        Action logs
            }

exec        ExecDTO {
            <em>description: OpenWhisk Action exec details</em>
            
            kind    string
            Action kind

            binary  boolean
                    <em>default: false</em>
                    Is action binary

            components  [
                        Action components in case of sequence
                        string]
            }
url         string
            Action url
}]
</code></pre>
            </td>
        </tr>
        <tr>
        <td><code>Authorization</code> (<code>string</code>: <em>header</em>)</td>
        <td>Authorization token in format: <code>Bearer {token}</code></td>
        </tr>
        <tr>
        <td><code>X-Api-Key</code> (<code>string</code>: <em>header</em>)</td>
        <td>Api key</td>
        </tr>
    </tbody>
</table>

#### _Responses:_
Response content type: `application/json`
| Code | Description |
|---|---|
| _default_ | Successful operation |

### GET /runtime/namespaces/{orgId}/{intId}/actions/{name}
Returns the details of an action.

#### _Parameters:_
| Name | Description |
|---|---|
| `orgId` (`string`: _path_) | Organization ID |
| `intId` (`string`: _path_) | Integration ID |
| `name` (`string`: _path_) | Action name |
| `Authorization` (`string`: _header_) | Authorization token in format: `Bearer {token}` |
| `X-Api-Key` (`string`: _header_) | Api key |

#### _Responses:_
Response content type: `application/json`
<table>
    <thead>
        <tr>
            <th>Code</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td style="vertical-align:top">200</td>
            <td><em>Successful operation</em> <br />Example value:
<pre><code>{
  "name": "string",
  "namespace": "string",
  "activationId": "string",
  "annotations": [
    {
      "key": "string",
      "value": {}
    }
  ],
  "duration": 0,
  "version": "string",
  "response": {}
}</code></pre>
Model: 
<pre><code>[ActionDTO {
<em>description: OpenWhisk Action</em>

name        string
            Action name
code        string
            Action code
namespace   string
            Action namespace
version     string
            Action version
params      [Action params
            KeyValuePairDTO {
            <em>description: OpenWhisk Action param</em>
            
            key     string
                    Param Name

            value   {
                        <em>description: Param value</em>
                    }
            }]

annotations [Action annotations
            KeyValuePairDTO {
            <em>description: OpenWhisk Action param</em>
            
            key     string
                    Param Name

            value   {
                        <em>description: Param value</em>
                    }
            }]

limits      LimitsDTO {
            <em>description: OpenWhisk Action Limits</em>
            
            timeout     string
                        Action timeout
            
            memory      string
                        Action memory limit

            logs        string
                        Action logs
            }

exec        ExecDTO {
            <em>description: OpenWhisk Action exec details</em>
            
            kind    string
            Action kind

            binary  boolean
                    <em>default: false</em>
                    Is action binary

            components  [
                        Action components in case of sequence
                        string]
            }
url         string
            Action url
}]
</code></pre>
            </td>
        </tr>
    </tbody>
</table>

### POST /runtime/namespaces/{orgId}/{intId}/actions/{name}
Executes an action.

#### _Parameters:_
| Name | Description |
|---|---|
| `orgId` (`string`: _path_) | Organization ID |
| `intId` (`string`: _path_) | Integration ID |
| `name` (`string`: _path_) | Action name |
| `Authorization` (`string`: _header_) | Authorization token in format: `Bearer {token}` |
| `X-Api-Key` (`string`: _header_) | Api key |

#### _Responses:_
Response content type: `application/json`
<table>
    <thead>
        <tr>
            <th>Code</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td style="vertical-align:top">200</td>
            <td><em>Successful operation</em> <br />Example value:
<pre><code>{
  "name": "string",
  "code": "string",
  "namespace": "string",
  "version": "string",
  "params": [
    {
      "key": "string",
      "value": {}
    }
  ],
  "annotations": [
    {
      "key": "string",
      "value": {}
    }
  ],
  "limits": {
    "timeout": "string",
    "memory": "string",
    "logs": "string"
  },
  "exec": {
    "kind": "string",
    "binary": false,
    "components": [
      "string"
    ]
  },
  "url": "string"
}</code></pre>
Model: 
<pre><code>[ActionResultDTO {
<em>description: OpenWhisk Action invocation result</em>

name        string
            Action name
code        string
            Action code
namespace   string
            Action namespace
version     string
            Action version

annotations [Action annotations
            KeyValuePairDTO {
            <em>description: OpenWhisk Action param</em>
            
            key     string
                    Param Name

            value   {
                        <em>description: Param value</em>
                    }
            }]
duration    integer($int32)
            Duration

version     string
            Action Version

response    {
            description:    
            Action invocation response
}
</code></pre>
            </td>
        </tr>
    </tbody>
</table>

### PUT /runtime/namespaces/{orgId}/{intId}/actions/{name}
Updates an action.

#### _Parameters:_
<table>
    <thead>
        <tr>
            <th>Name</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
        <td><code>orgId</code> (<code>string</code>: <em>path</em>)</td>
        <td>Organization ID</td>
        </tr>
        <tr>
        <td><code>intId</code> (<code>string</code>: <em>path</em>)</td>
        <td>Integration ID</td>
        </tr>
        <tr>
        <td><code>name</code> (<code>string</code>: <em>path</em>)</td>
        <td>Action name</td>
        </tr>
        <tr>
        <td style="vertical-align:top"><code>body</code> (<em>body</em>)</td>
        <td>Action form. <br> Example value: 
<pre><code>{
  "name": "string",
  "code": "string",
  "namespace": "string",
  "version": "string",
  "params": [
    {
      "key": "string",
      "value": {}
    }
  ],
  "annotations": [
    {
      "key": "string",
      "value": {}
    }
  ],
  "limits": {
    "timeout": "string",
    "memory": "string",
    "logs": "string"
  },
  "exec": {
    "kind": "string",
    "binary": false,
    "components": [
      "string"
    ]
  },
  "url": "string"
}</code></pre>Parameter content type: <code>application/json</code>
Model: 
<pre><code>[ActionDTO {
<em>description: OpenWhisk Action</em>

name        string
            Action name
code        string
            Action code
namespace   string
            Action namespace
version     string
            Action version
params      [Action params
            KeyValuePairDTO {
            <em>description: OpenWhisk Action param</em>
            
            key     string
                    Param Name

            value   {
                        <em>description: Param value</em>
                    }
            }]

annotations [Action annotations
            KeyValuePairDTO {
            <em>description: OpenWhisk Action param</em>
            
            key     string
                    Param Name

            value   {
                        <em>description: Param value</em>
                    }
            }]

limits      LimitsDTO {
            <em>description: OpenWhisk Action Limits</em>
            
            timeout     string
                        Action timeout
            
            memory      string
                        Action memory limit

            logs        string
                        Action logs
            }

exec        ExecDTO {
            <em>description: OpenWhisk Action exec details</em>
            
            kind    string
            Action kind

            binary  boolean
                    <em>default: false</em>
                    Is action binary

            components  [
                        Action components in case of sequence
                        string]
            }
url         string
            Action url
}]
</code></pre>
            </td>
        </tr>
        <tr>
        <td><code>Authorization</code> (<code>string</code>: <em>header</em>)</td>
        <td>Authorization token in format: <code>Bearer {token}</code></td>
        </tr>
        <tr>
        <td><code>X-Api-Key</code> (<code>string</code>: <em>header</em>)</td>
        <td>Api key</td>
        </tr>
    </tbody>
</table>

#### _Responses:_
Response content type: `application/json`
| Code | Description |
|---|---|
| _default_ | Successful operation |

### DELETE /runtime/namespaces/{orgId}/{intId}/actions/{name}
Deletes an action.

#### _Parameters:_
| Name | Description |
|---|---|
| `orgId` (`string`: _path_) | Organization ID |
| `intId` (`string`: _path_) | Integration ID |
| `name` (`string`: _path_) | Action name |
| `Authorization` (`string`: _header_) | Authorization token in format: `Bearer {token}` |
| `X-Api-Key` (`string`: _header_) | Api key |

#### _Responses:_
Response content type: `application/json`
| Code | Description |
|---|---|
| _default_ | Successful operation |

### GET /runtime/system/actions
Returns a list of built-in actions.

#### _Parameters:_
| Name | Description |
|---|---|
| `Authorization` (`string`: _header_) | Authorization token in format: `Bearer {token}` |
| `X-Api-Key` (`string`: _header_) | Api key |

#### _Responses:_
Response content type: `application/json`
<table>
    <thead>
        <tr>
            <th>Code</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td style="vertical-align:top">200</td>
            <td><em>Successful operation</em><br />Example value:
<pre><code>[
  {
    "name": "string",
    "code": "string",
    "namespace": "string",
    "version": "string",
    "params": [
      {
        "key": "string",
        "value": {}
      }
    ],
    "annotations": [
      {
        "key": "string",
        "value": {}
      }
    ],
    "limits": {
      "timeout": "string",
      "memory": "string",
      "logs": "string"
    },
    "exec": {
      "kind": "string",
      "binary": false,
      "components": [
        "string"
      ]
    },
    "url": "string"
  }
]</code></pre>
Model: 
<pre><code>[ActionDTO {
<em>description: OpenWhisk Action</em>

name        string
            Action name
code        string
            Action code
namespace   string
            Action namespace
version     string
            Action version
params      [Action params
            KeyValuePairDTO {
            <em>description: OpenWhisk Action param</em>
            
            key     string
                    Param Name

            value   {
                        <em>description: Param value</em>
                    }
            }]

annotations [Action annotations
            KeyValuePairDTO {
            <em>description: OpenWhisk Action param</em>
            
            key     string
                    Param Name

            value   {
                        <em>description: Param value</em>
                    }
            }]

limits      LimitsDTO {
            <em>description: OpenWhisk Action Limits</em>
            
            timeout     string
                        Action timeout
            
            memory      string
                        Action memory limit

            logs        string
                        Action logs
            }

exec        ExecDTO {
            <em>description: OpenWhisk Action exec details</em>
            
            kind    string
            Action kind

            binary  boolean
                    <em>default: false</em>
                    Is action binary

            components  [
                        Action components in case of sequence
                        string]
            }
url         string
            Action url
}]
</code></pre>
            </td>
        </tr>
    </tbody>
</table>

### POST /runtime/namespaces/{orgId}/{intId}/handleEventRegistration
Registers an event registration and assigns a given action to the event.

#### _Parameters:_
<table>
    <thead>
        <tr>
            <th>Name</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
        <td><code>orgId</code> (<code>string</code>: <em>path</em>)</td>
        <td>Organization ID</td>
        </tr>
        <tr>
        <td><code>intId</code> (<code>string</code>: <em>path</em>)</td>
        <td>Integration ID</td>
        </tr>
        <tr>
        <td style="vertical-align:top"><code>body</code> (<em>body</em>)</td>
        <td>Example value: 
<pre><code>{
  "id": "string",
  "name": "string",
  "description": "string",
  "client_id": "string",
  "type": "string",
  "integration_status": "string",
  "delivery_type": "string",
  "webhook_url": "string",
  "events_of_interest": [
    {
      "event_code": "string",
      "provider": "string"
    }
  ],
  "runtime_action": "string",
  "registration_id": "string"
}</code></pre>Parameter content type: <code>application/json</code>
Model: 
<pre><code>EventDTO {
<em>description: Adobe I/O Event Details</em>

id                  string
                    Event id
name                string
                    Event name
description         string
                    Event code
Client id           string
                    Event namespace
type                string
                    Event type

integration_status  string
                    Event integration status

delivery_type       string
                    Event delivery type

webhook_url         string
                    Webhook url

events_of_interest  [
                    Events of interest to listen to

                    EventsOfInterestDTO{
                    <em>description: Events of interest</em>

                        event_code  string
                                    Event code

                        provider    string
                                    Event provider
                    }]
runtime_action      string
                    Action to handle event

registration_id     string
                    Event registration id
}
</code></pre>
            </td>
        </tr>
        <tr>
        <td><code>Authorization</code> (<code>string</code>: <em>header</em>)</td>
        <td>Authorization token in format: <code>Bearer {token}</code></td>
        </tr>
        <tr>
        <td><code>X-Ams-Consumer-Id</code> (<code>string</code>: <em>header</em>)</td>
        <td>AMS consumer ID</td>
        </tr>
        <tr>
        <td><code>X-Ams-Application-Id</code> (<code>string</code>: <em>header</em>)</td>
        <td>AMS application ID</td>
        </tr>
        <tr>
        <td><code>X-Api-Key</code> (<code>string</code>: <em>header</em>)</td>
        <td>Api key</td>
        </tr>
    </tbody>
</table>

#### _Responses:_
Response content type: `application/json`
<table>
    <thead>
        <tr>
            <th>Code</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td style="vertical-align:top">200</td>
            <td><em>Successful operation</em> <br />Example value:
<pre><code>{
  "id": "string",
  "name": "string",
  "description": "string",
  "client_id": "string",
  "type": "string",
  "integration_status": "string",
  "delivery_type": "string",
  "webhook_url": "string",
  "events_of_interest": [
    {
      "event_code": "string",
      "provider": "string"
    }
  ],
  "runtime_action": "string",
  "registration_id": "string"
}</code></pre>
Model: 
<pre><code>EventDTO {
<em>description: Adobe I/O Event Details</em>

id                  string
                    Event id
name                string
                    Event name
description         string
                    Event code
Client id           string
                    Event namespace
type                string
                    Event type

integration_status  string
                    Event integration status

delivery_type       string
                    Event delivery type

webhook_url         string
                    Webhook url

events_of_interest  [
                    Events of interest to listen to

                    EventsOfInterestDTO{
                    <em>description: Events of interest</em>

                        event_code  string
                                    Event code

                        provider    string
                                    Event provider
                    }]
runtime_action      string
                    Action to handle event

registration_id     string
                    Event registration id
}
</code></pre>
            </td>
        </tr>
    </tbody>
</table>

### DELETE /runtime/namespaces/{orgId}/{intId}/handleEventDeletion/{clientId}/{registrationId}
Deletes an event registration.

#### _Parameters:_
| Name | Description |
|---|---|
| `orgId` (`string`: _path_) | Organization ID |
| `intId` (`string`: _path_) | Integration ID |
| `clientId ` (`string`: _path_) | IMS client ID |
| `registrationId` (`string`: _path_) | ID of registration |
| `X-Ams-Consumer-Id` (`string`: _path_) | AMS consumer ID |
| `X-Ams-Application-Id` (`string`: _path_) | AMS application ID |
| `Authorization` (`string`: _header_) | Authorization token in format: `Bearer {token}` |
| `X-Api-Key` (`string`: _header_) | Api key |

#### _Responses:_
Response content type: `application/json`
| Code | Description |
|---|---|
| _default_ | Successful operation |

### PUT /runtime/namespaces/{orgId}/{intId}/handleEventUpdate/{clientId}/{registrationId}
Updates an event registration.

#### _Parameters:_
<table>
    <thead>
        <tr>
            <th>Name</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
        <td><code>orgId</code> (<code>string</code>: <em>path</em>)</td>
        <td>Organization ID</td>
        </tr>
        <tr>
        <td><code>intId</code> (<code>string</code>: <em>path</em>)</td>
        <td>Integration ID</td>
        </tr>
        <tr>
        <td><code>clientId</code> (<code>string</code>: <em>path</em>)</td>
        <td>IMS client ID</td>
        </tr>
        <tr>
        <td><code>registrationId</code> (<code>string</code>: <em>path</em>)</td>
        <td>Registration ID</td>
        </tr>
        <tr>
        <td><code>X-Ams-Consumer-Id</code> (<code>string</code>: <em>header</em>)</td>
        <td>AMS consumer ID</td>
        </tr>
        <tr>
        <td><code>X-Ams-Application-Id</code> (<code>string</code>: <em>header</em>)</td>
        <td>AMS application ID</td>
        </tr>
        <tr>
        <td style="vertical-align:top"><code>body</code> (<em>body</em>)</td>
        <td>Example value: 
<pre><code>{
  "id": "string",
  "name": "string",
  "description": "string",
  "client_id": "string",
  "type": "string",
  "integration_status": "string",
  "delivery_type": "string",
  "webhook_url": "string",
  "events_of_interest": [
    {
      "event_code": "string",
      "provider": "string"
    }
  ],
  "runtime_action": "string",
  "registration_id": "string"
}</code></pre>Parameter content type: <code>application/json</code>
Model: 
<pre><code>EventDTO {
<em>description: Adobe I/O Event Details</em>

id                  string
                    Event id
name                string
                    Event name
description         string
                    Event code
Client id           string
                    Event namespace
type                string
                    Event type

integration_status  string
                    Event integration status

delivery_type       string
                    Event delivery type

webhook_url         string
                    Webhook url

events_of_interest  [
                    Events of interest to listen to

                    EventsOfInterestDTO{
                    <em>description: Events of interest</em>

                        event_code  string
                                    Event code

                        provider    string
                                    Event provider
                    }]
runtime_action      string
                    Action to handle event

registration_id     string
                    Event registration id
}
</code></pre>
            </td>
        </tr>
        <tr>
        <td><code>Authorization</code> (<code>string</code>: <em>header</em>)</td>
        <td>Authorization token in format: <code>Bearer {token}</code></td>
        </tr>
        <tr>
        <td><code>X-Api-Key</code> (<code>string</code>: <em>header</em>)</td>
        <td>Api key</td>
        </tr>
    </tbody>
</table>

#### _Responses:_
Response content type: `application/json`
<table>
    <thead>
        <tr>
            <th>Code</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td style="vertical-align:top">200</td>
            <td><em>Successful operation</em> <br />Example value:
<pre><code>{
  "id": "string",
  "name": "string",
  "description": "string",
  "client_id": "string",
  "type": "string",
  "integration_status": "string",
  "delivery_type": "string",
  "webhook_url": "string",
  "events_of_interest": [
    {
      "event_code": "string",
      "provider": "string"
    }
  ],
  "runtime_action": "string",
  "registration_id": "string"
}</code></pre>
Model: 
<pre><code>EventDTO {
<em>description: Adobe I/O Event Details</em>

id                  string
                    Event id
name                string
                    Event name
description         string
                    Event code
Client id           string
                    Event namespace
type                string
                    Event type

integration_status  string
                    Event integration status

delivery_type       string
                    Event delivery type

webhook_url         string
                    Webhook url

events_of_interest  [
                    Events of interest to listen to

                    EventsOfInterestDTO{
                    <em>description: Events of interest</em>

                        event_code  string
                                    Event code

                        provider    string
                                    Event provider
                    }]
runtime_action      string
                    Action to handle event

registration_id     string
                    Event registration id
}
</code></pre>
            </td>
        </tr>
    </tbody>
</table>

### POST /runtime/namespaces/{orgId}/{intId}/handleEventStatus/{clientId}/{registrationId}/{status}
Updates the status of an event registration.

#### _Parameters:_
| Name | Description |
|---|---|
| `orgId` (`string`: _path_) | Organization ID |
| `intId` (`string`: _path_) | Integration ID |
| `clientId ` (`string`: _path_) | IMS client ID |
| `registrationId` (`string`: _path_) | ID of registration |
| `status` (`string`: _path_) | Status of the registration |
| `X-Ams-Consumer-Id` (`string`: _path_) | AMS consumer ID |
| `X-Ams-Application-Id` (`string`: _path_) | AMS application ID |
| `Authorization` (`string`: _header_) | Authorization token in format: `Bearer {token}` |
| `X-Api-Key` (`string`: _header_) | Api key |

#### _Responses:_
Response content type: `application/json`
<table>
    <thead>
        <tr>
            <th>Code</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td style="vertical-align:top">200</td>
            <td><em>Successful operation</em> <br />Example value:
<pre><code>{
  "id": "string",
  "name": "string",
  "description": "string",
  "client_id": "string",
  "type": "string",
  "integration_status": "string",
  "delivery_type": "string",
  "webhook_url": "string",
  "events_of_interest": [
    {
      "event_code": "string",
      "provider": "string"
    }
  ],
  "runtime_action": "string",
  "registration_id": "string"
}</code></pre>
Model: 
<pre><code>EventDTO {
<em>description: Adobe I/O Event Details</em>

id                  string
                    Event id
name                string
                    Event name
description         string
                    Event code
Client id           string
                    Event namespace
type                string
                    Event type

integration_status  string
                    Event integration status

delivery_type       string
                    Event delivery type

webhook_url         string
                    Webhook url

events_of_interest  [
                    Events of interest to listen to

                    EventsOfInterestDTO{
                    <em>description: Events of interest</em>

                        event_code  string
                                    Event code

                        provider    string
                                    Event provider
                    }]
runtime_action      string
                    Action to handle event

registration_id     string
                    Event registration id
}
</code></pre>
            </td>
        </tr>
    </tbody>
</table>