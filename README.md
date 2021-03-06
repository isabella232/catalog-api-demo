# Catalog API Demo App

Demo app providing examples of common Catalog API interactions.

## Assumptions

This README assumes you are using Maven to build and run Java code. If you are
not using Maven, the app should still work, but you will need to follow your
existing build/execution steps.

## STEP 1: Get a Personal Access Token

To execute the examples in this demo, you'll need a personal access token from
Square. If you already have one, you can use it for this demo. If you don't
already have one (or want to use a different one) you can generate a new access
token:

1. Visit the Application Dashboard at https://connect.squareup.com/apps
2. Click "New Application".
3. Create an application with the name "Catalog API Demo".
4. Copy the Personal Access Token that is generated and save it to an
  environment variable:
   
   `export SQPAT={{ YOUR NEW ACCESS TOKEN }}`

## STEP 2: Compile the demo

The `src` directory should contain everything you need to compile and run the
demo app. To build `catalog-api-demo`:

```
mvn compile
```

## STEP 3: List the available examples

To confirm the demo is runnable, use the `-list-examples` flag to see all
the available examples:

```
mvn -q exec:java "-Dexec.args=-list-examples"
```

## Execute an Example

Source code for each of the examples is listed under
`src/main/java/com/squareup/catalog/demo/example/`.

Running an example has the following syntax:

```
mvn -q exec:java "-Dexec.args={{ example name }} -token {{ accessToken }}"
```

For example:
```
mvn -q exec:java "-Dexec.args=create_item -token $SQPAT"
```

## Cleanup an Example

Some examples create items and other catalog objects in your merchant catalog. You can
cleanup the objects created by an example using the `-cleanup` flag.

Note that the cleanup code will delete items and other objects by name, and as such may
delete items with the same name that were not created by the example. 

For example:
```
mvn -q exec:java "-Dexec.args=create_item -token $SQPAT -cleanup"
```