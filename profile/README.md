# Nuxt Service Layers

This is an attempt at using nuxt layers to modularise complex functionality for rapid development. I
imagine this will be most useful when constructing small scale apps that only need common features.
There is of course a trade off between flexability and development speed.

## Services

This project is in its birthing stage the this list is very limeted and has limeted support of
database types.

The plan is for each service to have a set of code interactions for any type of database allowing
for very versatile usage and rapid implementaion.

##### Users

This will provide the app with a global $User pinia store that can be used to add and manipulate
users. The plan is to have it provide all the nessersary manipulations for the user and handle
seemlessly the logged in user.

##### Notifications

To provide a notification system allowing for emails, sms and in app notifications.

##### Payments

Speed up payment integration with your app with a payment layer. This should handle different
payment providers and store payment information in the database.

## Getting started

Simply fire up the dev container I have provided.

##### Database Connection

In your `services.config.ts` choose your database type:

```ts
const servicesConfig: ServiceLayerConfig = {
	database: "firestore" | "postgres" | "mongo" | "sqlite",
}
```

Then add the details to the .env file provided.

##### Adding Services

In your `services.config.ts` simply add the service to the service array:

```ts
const servicesConfig: ServiceLayerConfig = {
	services: [
		{ name: "users", version: "1.0.0" },
		{ name: "notifications", version: "1.0.0" },
	],
}
```

#### Layer Diagram

Here I have made a diagram. As you can see your project app only needs to interface directly with
the services. Which can be selected in the `services.config.ts`. All the rest happens under the
hood.

![Diagram of the layer stack](./assets/stack-diagram.png)
