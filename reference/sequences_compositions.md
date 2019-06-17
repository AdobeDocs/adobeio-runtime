# Sequences and Compositions

Sometimes you want to orchestrate a series of action calls into a flow. There are two ways to do this: using sequences or compositions.

Sequences represent a single string of actions that are invoked in sequence, starting with the first one, then second, and so forth until the last one. At each step the result of the current action feeds into the arguments of the next one. There is no support to skip one action.

If you want to execute a tree of actions, where you want to be able to evaluate the result of an action and depending on it execute a different action (think of an if/else control structure) then compositions are your best friend.

## Sequences

Assuming that you have two actions created in a package called `my-package`:
```
/my-package/actionA
/my-package/actionB
```

You can create a sequence using the `--sequence` flag in addition to the usual command for creating an action (make sure you add the namespace to the action name; otherwise you'd see an error about not being authorized to access those resources):
`wsk action create mySequence --sequence /[your-namespace]/my-package/actionA,/[your-namespace]/my-package/actionB`

You can invoke this as any other action. For example:
`wsk action invoke --result mySequence`

You can read more about sequences on the [OpenWhisk documentation page](https://github.com/apache/incubator-openwhisk/blob/master/docs/actions.md#creating-action-sequences).

## Compositions

For the time being, compositions are not supported by I/O Runtime. We will enable this feature soon.