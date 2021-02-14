# Code generation

generated with command
docker run --rm -v "${PWD}:/local" openapitools/openapi-generator-cli generate \
    -i /local/openapi.yaml \
    -g go-server \
    -o /local/server

mmhh