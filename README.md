# Macellum API Client Library TypeScript

This repository hosts a TypeScript library that serves as a client for the Macellum API, adhering to the [Macellum API Specification](https://github.com/alexandrelamberty/macellum-api-spec). This library is designed to facilitate interactions with the API, primarily for integration into projects like [Macellum](https://github.com/alexandrelamberty/macellum) project.

## Installation

You can install the library via package manager. For example, using `pnpm`:

```shell
pnpm install --save @alexandrelamberty/macellum-api-client-typescript
```

## Usage

Here's a basic example demonstrating how to use the library:

```ts
import Macellum from "@alexandrelamberty/macellum-api-client-typescript";

const macellum = new Macellum({
    apiKey: "YOUR_API_KEY"
})

macellum.analytics.get()
```

## Development

- **Generating Source Code:** To generate source code from the OpenAPI specification, run:

    ```shell
    pnpm api
    ```

    This command uses `openapi-generator-cli` to generate TypeScript code based on the provided API specification file.

- Running Tests: Execute the following command to run tests:

    ```shell
    pnpm test
    ```

### Linking library locally

During development, you might want to test your changes in other projects without publishing to npm. You can do this by linking the library locally:

```shell
pnpm link --global
```

This command globally links the local version of the library, allowing you to use it in other projects as if it were installed from npm.

### Documentation

Documentation for this library is generated using Typedoc. To generate HTML documentation, use:

```bash
pnpm doc:html
```

This generates HTML documentation in the `build/docs` directory. You can then open `index.html` in a browser to view the documentation locally. Additionally, you can publish the documentation to GitHub Pages using:

```bash
pnpm doc:publish
```

This command publishes the documentation to the gh-pages branch of the repository, making it accessible via the project's GitHub Pages URL.

## GitHub Actions

This project utilizes GitHub Actions for automating the release and publishing process. Below is the workflow defined in the `.github/workflows/release-publish.yml`

This workflow consists of two jobs:

1. Release: This job creates a GitHub release whenever a new tag is pushed to the repository.

2. Publish: This job publishes the package to npm and GitHub Packages after the release job is completed successfully.

Before using this workflow, ensure you have set up the necessary secrets in your repository settings:

- **GITHUB_TOKEN:** Required for creating GitHub releases.

- **NPM_TOKEN:** Required for publishing to npm.
