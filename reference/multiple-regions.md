# Multiple Regions

Today, we execute your actions in two Amazon regions: US-East, Europe-West, and Australia. We have plans to add aditional regions in Amazon and add Azure support too.

## How do we execute your action

When you deploy an action, we push your code to all the regions. At execution time, we use a latency-based routing policy to decide where to execute your action: we run it in the closest region to the client who invoke it. 

In the event that a region goes down, then your invocations will be directed to the next closest region.

There is nothing you need to do in order to execute your action in the closest region to your app. There is also no flag to restrict an action to a specific region.

## How do I know in what region my actions are executed

We make available the information about the cloud and region where action is being executed at execution time. Within your action, this is how you can retrieve cloud and region values:

```
// this could output aws
process.env['__OW_CLOUD']

// this could output us-east-1
process.env['__OW_REGION']
```

Please note, that regions can change (failover or permanent changes). Your application should not work against a hard-coded set of regions and should handle the case when the region you are looking for is not the region where your action is being executed.

