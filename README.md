# Build Node service image

Builds a Node service Docker image.

- Runs the Docker Compose `serviceBuilder` component. This component normally should:
    - Test the code
    - Lint the code
    - Transpile the TypeScript to JavaScript
- Builds the Docker image and names it `service`.

Required environment variables:
```sh
# The npm token to use authenticate to pull the private @qompium packages
NPM_TOKEN=....
```

Example usage:
```yaml
jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repository
        uses: actions/checkout@v2

      - name: Test and build Docker image
        uses: QActions/build-node-service-image@1.0.0
        env:
          NPM_TOKEN: ${{ secrets.NPM_TOKEN }}
```
