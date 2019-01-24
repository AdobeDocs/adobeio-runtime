# Throughput Tuning

The main instrument you can use for tuning how a given action is executed and enable a faster number of executions, is the value you set for the `action/container concurrency`. This value is not related to the concurrent value per namespace or minuteRate value, though these two enforce the upper limit for actions executed per minute your namespace can reach.

The default value is `1` and it means that 1 invocation can happen in the same container for the that action. Suppose that you want to execute 100 times a `HelloWorld` action at the same time or in short period of time (minutes). With the default value (`1`) it means that the system will use 100 different containers instead of using the same container.

This enables you to avoid cold-start issues. When the system doesn't have any containers left, it has to create new ones. This cold-start adds a lot of latency to your application.

You can set any value between `1` and `10.000`. In the example below, the limit is set to `200`:
```
wsk action create actionName fileName.js -c 200
```

Some considerations to keep in mind:
1. A container is kept warm after an invocation finished for 10 minutes. This means that for 10 minutes you can be 99% you don't get cold-starts when executing the same action
2. Depending on how much memory/resources your action consumes, you can use a smaller or a higher value. A good average number to start with is `200`. You should experiment to make sure the value you choose is working 
3. Make sure that your code is working when being executed in parallel. Using global variables to store values that are different between invocations is a recipe for disaster
4. If your Action works on some large data that is not different between invocations, then using a global variable can maximize the chances that the next execution can reuse it. However your code should handle the situation where the variable is not initialized
5. It is not guarantee that all invocations will use the same container. In case of errors, the existing container is destroyed and a new container will be used
6. In cases where your action code is memory hungry, you might need to tweak this setting to a lower value 

## Caching Responses

The second instrument you have to maximize throughput is caching the action response. When you cache an action response, for the time the cache is valid, you can invoke the action without increasing the counter used by minuteRate or concurrent action invocations per namespace. In this situations, your action is not actually executed, instead the system serves the result from cache.

You use the Cache-Control dirrective in order to configure the cache.