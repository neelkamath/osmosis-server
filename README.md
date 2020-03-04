# Backend Prototype

_Quick reliable backend prototypes_

![Cover](cover.jpg)

For backend developers who need to build a prototype, this project is a template that provides boilerplate for the required technologies. Unlike other templates, this project provides the best technologies for prototyping modern applications.

To know why particular technologies were chosen, read the [explanation](docs/explanation.md).

You might want to create a separate repository to host the specification(s) such as the frontend's wireframes, the application's objectives, the OpenAPI specification, etc. In that case, remove the OpenAPI parts of this repo.

If you're using this template for a hackathon, feel free to set up your project prior to the event. Setting up non-program assets such as CI/CD pipelines isn't against the rules.

Follow the **Contributing** section if you are using this template (building the HTTP API; the backend developer) to create an application. Follow the **Installation** and **Usage** sections if you are using the application (consuming the HTTP API; the frontend developer) that was built with this template.

## Installation

Optionally, generate a client SDK for the HTTP API using [OpenAPI Generator](https://openapi-generator.tech/) on the file https://raw.githubusercontent.com/neelkamath/backend-prototype/master/docs/openapi.yaml.

## Usage

The HTTP API's base URL is https://backend-prototype.herokuapp.com/. You can read the [documentation](https://neelkamath.gitlab.io/backend-prototype/).

## Contributing

### Installation

1. [Use this template](https://github.com/neelkamath/backend-prototype/generate).
1. Clone the repository using one of the following methods.
    - SSH: `git clone git@github.com:neelkamath/backend-prototype.git`
    - HTTPS: `git clone https://github.com/neelkamath/backend-prototype.git`
1. Read [this gist](https://gist.github.com/neelkamath/df9198b13ac344b17938a7909cdb31f2) to learn how to set up projects.
1. Install [Docker](https://hub.docker.com/search/?type=edition&offering=community).
1. Install the latest [node.js LTS](https://nodejs.org/en/download/).
1. Set up the DB.
    1. Create a [Heroku](https://heroku.com/) app.
    1. Provision the [mLab add-on](https://elements.heroku.com/addons/mongolab).
    1. Retrieve the `MONGODB_URI` connection string from your Heroku app's config vars. Save it for later.
    1. Create a file named `.env`.
    1. Add the line `MONGODB_URI=<URI>` to `.env`. Replace `<URI>` with the connection string you retrieved earlier.
1. Set up the CI/CD pipeline.
    1. Create a [GitLab account](https://gitlab.com/users/sign_up).
    1. [Connect](https://docs.gitlab.com/ee/ci/ci_cd_for_external_repos/github_integration.html) the GitHub repo to a GitLab repo.
1. Optionally, generate a server stub for the HTTP API using [OpenAPI Generator](https://openapi-generator.tech/) on the file https://raw.githubusercontent.com/neelkamath/backend-prototype/master/docs/openapi.yaml.

### [Developing](docs/developing.md)

### DB Schema

We use MongoDB. There is one MongoDB collection named `names`. Every MongoDB document in the collection contains a single name in the format `{"name": "<NAME>"}` (where `<NAME>` is a name such as `Neel`). No duplicate names are to be allowed.

## License

This project is under the [MIT License](LICENSE).