# Creating REST APIs

You can create REST APIs from web actions you&rsquo;ve deployed to Adobe I/O Runtime. Let&rsquo;s assume that you&rsquo;ve created four actions to manage CRUD operations for the `pet` entity:


|CRUD Operation | Action Name |
|---|---|
| Create | `addPet` |
| Read | `getPet` |
| Update  | `updatePet` |
| Delete  | `deletePet` |

You can map these actions to a REST API for managing `pet` resources:

| Endpoint | HTTP Method | Action Nam |
|---|---| --- |
| /pet | POST | `addPet` |
| /pet | GET | `getPet` |
| /pet/{id} | GET | `getPet` |
| /pet/{id} | PUT | `updatePet` |
| /pet/{id} | DELETE | `deletePet` |

Let&rsquo;s see how you can create this API, assuming you have the web actions are already deployed/created.

## Using wsk CLI

Using the `wsk api create` command, you create each API endpoint one-by-one. This command allows you to set a base path, path, method, and response type. We will set:

```
wsk api create /pet-store /pet post createPet --response-type http
wsk api create /pet-store /pet get getPet --response-type http
wsk api create /pet-store /pet/{id} get getPet --response-type http
wsk api create /pet-store /pet/{id} put updatePet --response-type http
wsk api create /pet-store /pet/{id} delete deletePet --response-type http
```
You can quickly see the API you&rsquo;ve defined, including the fully qualified path, by running this command:
```
wsk api list /pet-store
```

Please note, that at this time `wsk api list` is not implemented. Instead, you have to use `wsk api list /enter-base-path`.

Here is an example of calling one of the endpoints:
```
curl https://adobeioruntime.net:443/apis/<YOUR-NAMESPACE>/pet-store/pet/2345 -X get
```
or
```
curl https://<YOUR-NAMESPACE>.adobeioruntime.net:443/apis/pet-store/pet/2345 -X GET
```
**Note** the change in the URL here in comparison to what the `wsk` returns. This is due some additional protections Runtime provides to segregate namespaces from each other when invoking web actions. The `wsk` generated link will still work but it will return a 308 redirect to your namespace's subdomain on Runtime. For a further discussion of this please see the [Securing Web Actions](securing_web_actions.md) page.

In the example above, the `{di}` value, 2335, will be mapped to a {payload.id}.


## Using Swagger files

A neat feature when working with REST APIs is the support for Swagger files. This works for creating a new REST API from scratch or, if you already used the `wsk` CLI to create one,  saving the API as a Swagger definition file that you can use later on to restore the API.

Continuing the example above, if you run this command, you&rsquo;ll create a Swagger definition file on your machine out of the pet-store API:
```
wsk api get /pet-store > pet-store-swagger.json
```

Suppose that you want to restore or create the same API, maybe in some other namespace. All you have to is to run:
```
wsk api create --config-file pet-store-swagger.json
```
This will work as long as the actions are already created in that namespace.

## Securing the API edpoints

You secure an API the same way you&rsquo;d do it for web actions. You can read more about this on the [Securing Web Actions](securing_web_actions.md) page.

Once you&rsquo;ve enabled basic authentication for an action, you&rsquo;d have to pass the `X-Require-Whisk-Auth` header and the secret you chose when making an API call. 
