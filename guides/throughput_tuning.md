# Throughput Tuning

The main instrument you can use for tuning how a given action is executed and enable a higher number of executions for it, is the value you set for the `action/container concurrency`. This value is not related to the concurrent value per namespace or minuteRate value.

The default value is `1` and it means that only one action is invoked into a container at the same time. Suppose that you want to execute 100 times the HelloWorld action, at the same time or in short period of time (seconds/minutes). With the default value (`1`) it means that the system will use up to 100 different containers (some might be reused if the 100 invocations are not overlapping).

If you change the value to `100`, then the system will reuse a single container and execute all 100 invocations in the same container.

There is a second benefit for using a higher number: you get around of the cold-start issue. When the system doesn't have any containers left, it has to create new ones. This cold-start can add lot of latency to your application.

You can set any value between 1 and 10.000. In the example below, the limit is set to `200`:
```
wsk action create actionName fileName.js -c 200
```

Some considerations to keep in mind when you change the default value:
1. Depending on how much memory/resources your action consumes, you can use a smaller or a higher value. A good average number to start with is `500`. You should experiment to make sure the value you choose is working 
2. Make sure that your code is working when being executed in parallel. Using global variables to store values that are different between invocations is a recipe for disaster
3. If your Action works on some large data that is not different between invocations, then storring that data in a global variable can maximize the chances that the next execution can reuse it
 