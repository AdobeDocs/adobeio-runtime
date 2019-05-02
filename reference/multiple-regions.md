# Multiple Regions

Today, we execute your actions in two Amazon regions: US-East and Europe-West. We have plans to add aditional regions in Amazon and add Azure support too.

## How do we execute your action

When you deploy an action, we push your code to all the regions. At execution time, we use a latency-based routing policy to decide where to execute your action: we run it in the closest region to the client who invoke it. 

In the event that a region goes down, then your invocations will be directed to the next closest region.

There is nothing you need to do in order to execute your action in the closest region to your app. There is also no flag to restrict an action to a specific region.

## How do I know in what region my actions are executed

We have plans to add a new entry in the activation meta-data object that captures the regions and cloud where the that invocation was executed.

