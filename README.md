ember engines 0.7.1/ember-source 3.10 issue reproduction
========================================================

## setup

```sh
npm i -g ember-cli
mkdir engines-310
cd engines-310
ember new host-app --skip-git --skip-npm
ember new foo-engine -b https://github.com/ember-engines/engine-blueprint.git --skip-git --skip-npm
touch package.json # edit to make it a yarn workspace
yarn install
cd host-app
ember install ember-engines
# add routes to foo-engine and a link-to to a route
# mount foo-engine in host-app and add a link-to to enginer root
ember s
# click link to /foo-engine
```

## Error

```
index.js:163 Uncaught Error: Assertion Failed: You attempted to generate a link for the "foo.bar" route, but did not pass the models required for generating its dynamic segments. There is no route named foo.bar
    at assert (index.js:163)
    at Class.computeLinkToComponentHref (glimmer.js:2933)
    at ComputedProperty.get (metal.js:3112)
    at get (metal.js:1567)
    at RootPropertyReference.compute (glimmer.js:484)
    at RootPropertyReference.value (glimmer.js:343)
    at ComponentElementOperations.flush (runtime.js:1572)
    at Object.evaluate (runtime.js:986)
    at AppendOpcodes.evaluate (runtime.js:70)
    at LowLevelVM.evaluateSyscall (runtime.js:3269)
```
