# Swagger Codegen v3 Github Actions

This action runs [Swagger Codegen V3](https://github.com/swagger-api/swagger-codegen/tree/3.0.0) (through [this docker image](https://hub.docker.com/r/swaggerapi/swagger-codegen-cli-v3)) with Github Actions.

Template-driven engine to generate documentation, API clients and server stubs in different languages by parsing your OpenAPI / Swagger definition.

## Inputs

### `args`

**Required** Same arguments as [swagger-codegen-cli](https://github.com/swagger-api/swagger-codegen)

## Exemples

```yaml
jobs:
  generate-sdk:
    name: Generate a typescript sdk from https://raw.githubusercontent.com/OAI/OpenAPI-Specification/master/examples/v3.0/petstore.yaml
    runs-on: ubuntu-latest
    steps:
      - name: Generates sdk
        uses: johan-jnn/swagger-codegen-v3-action@master
        with:
          args: 'generate
            -i https://raw.githubusercontent.com/OAI/OpenAPI-Specification/master/examples/v3.0/petstore.yaml
            -o .
            -l typescript-node'

      - name: Exporting sdk to the sdk branch
        uses: ad-m/github-push-action@master
        with:
          branch: sdk
          force: true
```
