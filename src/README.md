# CROSSFIT APP

[Article Link](https://www.freecodecamp.org/news/rest-api-design-best-practices-build-a-rest-api/)

## Goal of the app

We'll build a REST API for a CrossFit Training Application. If you're not familiar with CrossFit, it's a fitness method and competitive sport that combines high-intensity workouts with elements from several sports (olympic weightlifting, gymnastics, and others).

In our application we'd like to create, read, update and delete WOD's (Workouts of the Day). This will help our users (that will be gym owners) come up with workout plans and maintain their own workouts inside a single application. On top of that, they also can add some important training tips for each workout.

## # Layer Architecture

![DataFlow](https://www.freecodecamp.org/news/content/images/2022/04/Bildschirmfoto-2022-04-25-um-14.33.24-1.png)

Inside the **Controller/Handler** we'll be handling all stuff that is related to HTTP. That means we're dealing with requests and responses for our endpoints.

Above that layer is also a little **Router** from Express that passes requests to the corresponding controller.

The whole business logic will be in the **Service** Layer that exports certain services (methods) which are used by the controller.

The third layer is the **Data Access** Layer where we'll be working with our Database. We'll be exporting some methods for certain database operations like creating a WOD that can be used by our Service Layer.

In our example we're not using a real database such as MongoDB or PostgreSQL because I'd like to focus more on the best practices itself. Therefore we're using a local JSON file that mimics our Database.

## Versioning

Like in other applications there will be improvements, new features, and stuff like that. So it's important to version our API as well.

The big advantage is that we can work on new features or improvements on a new version while the clients are still using the current version and are not affected by breaking changes.

We also don't force the clients to use the new version straight away. They can use the current version and migrate on their own when the new version is stable.

The current and new versions are basically running in parallel and don't affect each other.

## Name Resources in plural

controllers, services, handlers, routes

## Accept and respond with data in JSON format

Continue from here.

After all is done modify addresses in fetch api server side from 5000 to whichever is the current working one

It's also a good practice to name the service methods the same as the controller methods so that you have a connection between those.

Inside our service methods we'll be handling our business logic like transforming data structures and communicating with our Database Layer.

We're sending back data in JSON format. But what about accepting it? Let's think about an endpoint where we need to receive JSON data from the client. The endpoint for creating or updating a workout needs data from the client.

To be able to parse the sent JSON inside the request body, we need to install body-parser first and configure it.

`npm i body-parser`

`app.use(bodyParser.json());`

To improve the request validation you normally would use a third party package like express-validator.