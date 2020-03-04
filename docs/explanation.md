# Explanation

## ngrok

We use [ngrok](https://ngrok.com/product) to expose the server to the internet so that our fellow developers can consume the service. We will not host the server for the following reasons.
- The only free hosting service is Heroku, whose free tier runs out of memory unusably quickly. The other free tiered services, such as AWS, only provide a free trial for several months at best.
- It takes a longer time to deploy because of the slow pipeline. The pipeline is slow because it has to upload to multiple services, each of which has to redownload and recompile every dependency. It's difficult and time-wasting to set up caching for these pipeline components.
- Applications which are polyglot, or have even slightly unorthodox setups, require an excessive amount of non-standard configuration which isn't acceptible while prototyping.

## GitHub

[GitHub](https://github.com/) is an excellent platform for prototypes. It version controls your application using [Git](https://git-scm.com/) so that you can revert to what worked in a prior commit. It has a marketplace, free private repositories, enables you to share your project with collaborators and your future self, etc. 

## Gradle

[Gradle](https://gradle.org/) is the most advanced automation system. It automatically builds your Kotlin, Swift, JavaScript, etc. apps by bringing in dependencies (e.g., ktor), compilers (e.g., the Kotlin compiler), plugins (e.g., a GitHub release plugin, a Bintray release plugin), etc.

## Kotlin

[Kotlin](https://kotlinlang.org/) can seamlessly leverage one of the biggest ecosystems out there, namely the JVM. Its concise syntax, superior IDE support, REPL, and excellent tooling leave the complex configs and setups of Java in the past. Clearly, Kotlin isn't just production ready, but is an excellent language choice for building prototypes as well.

## Kotest

[Kotest](https://github.com/kotest/kotest) is similar to Kotlin's standard testing library, and also includes goodies such as hamcrest matchers which greatly improve error reporting while drastically cutting down on the amount of code that needs to be written. Testing core logic on the backend is done the easiest through automated test suites. In prototypes, test suites should be significantly smaller than their production equivalents.

## ktor

[ktor](http://ktor.io/) is an easy to use, fun, and asynchronous framework for building servers. It is foundationally strong, has support for everything from websockets to templating languages, and is trivial to set up.

## OpenAPI

[OpenAPI](https://www.openapis.org/) is an HTTP API specification tool which provides the following benefits.
- Only non-program assets (e.g., logos) may be created prior to a hackathon. By formally specifying which endpoints are to be created, the developer has a clearer idea of what will be built during the event.
- Using a tool like [OpenAPI Generator](https://openapi-generator.tech/), you can generate server stubs and client SDKs.
- Using a tool like [Redoc](https://github.com/Redocly/redoc), the frontend developer has access to the service's documentation.
- Using a tool like [Prism](https://github.com/stoplightio/prism), the frontend developer can make use of a mock server while the real one is being built.

## GitLab CI

[GitLab CI](https://docs.gitlab.com/ee/ci/) allows you to verify that your application works (continuous integration) even in an isolated environment (e.g., on Heroku), and then deploys it (continuous deployment). Unlike GitHub Actions, GitLab CI has better static pages support, package registries, etc.

## MongoDB

Although a production application would favor an RDBMS, prototypes simply require runtime objects to be persisted This is not the same thing as a traditional DB. Unlike advanced systems such as Postgres, the occasional corruption of data (which has a negligible chance of occurring during prototyping), and lack of features such as views, functions, and custom datatypes, is a nonissue. Since we're not storing real data (i.e., the DB is insensitive to security defects and data loss), [MongoDB](https://www.mongodb.com/)'s lack of schemas is a pro rather than a con. We can easily dump objects at runtime without having to worry about table creation, DB migrations, etc.

## mLab

We use [mLab](https://www.mlab.com/home) because it automatically sets up a DB. It also provides a GUI so that you can easily manipulate data (e.g., wipe the DB, create an entry).

## Docker

We use [Docker](https://www.docker.com/) because it provides the following benefits.
- In the dire scenario where another person must run the application, the program can be run with zero setup (with the exception of have Docker installed).
- It is not unusual for prototypes to turn into polyglots as the required functionality is only available in language-exclusive libraries. For example, a Go NLP library, and a Python Wikipedia library may be used. Althought it pays off in production-ready applications to wrap such libraries in a server, it does not make sense for prototypes to do so. Docker Compose allows us to easily connect any number of technologies with ease.
- Scripts, such as one to seed the DB, are not only cross-platform, but automated and reproducible as well, which are two very important features while prototyping.