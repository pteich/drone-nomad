# drone-nomad

Drone plugin for deployment with Nomad

## Build

Build the binary with the following command:

```console
export GOOS=linux
export GOARCH=amd64
export CGO_ENABLED=0
export GO111MODULE=on

go build -v -a -tags netgo -o build/linux/amd64/drone-nomad
```

## Docker

Build the Docker image with the following command:

```console
docker build \
  --label org.label-schema.build-date=$(date -u +"%Y-%m-%dT%H:%M:%SZ") \
  --label org.label-schema.vcs-ref=$(git rev-parse --short HEAD) \
  --file docker/Dockerfile.linux.amd64 --tag plugins/nomad .
```

## Usage

```console
docker run --rm \
  -v $(pwd):$(pwd) \
  -w $(pwd) \
  plugins/drone-nomad
```

## Template Variables

The following variables could be configured on a nomad template with the following syntax `${VAR_NAME}`.

| Variable | Description |
|---|---|
| PLUGIN_ADDR | nomad addr |
| PLUGIN_TOKEN | nomad token |
| PLUGIN_REGION | nomad region |
| PLUGIN_NAMESPACE | nomad namespace |
| PLUGIN_TEMPLATE | nomad template |
| DRONE_REPO_OWNER | repository owner |
| DRONE_REPO_NAME | repository name |
| DRONE_COMMIT_SHA | git commit sha |
| DRONE_COMMIT_REF | git commit ref |
| DRONE_COMMIT_BRANCH | git commit branch |
| DRONE_COMMIT_AUTHOR | git author name |
| DRONE_COMMIT_MESSAGE | commit message |
| DRONE_BUILD_EVENT | build event |
| DRONE_BUILD_NUMBER | build number |
| DRONE_BUILD_STATUS | build status |
| DRONE_BUILD_LINK | build link |
| DRONE_BUILD_STARTED | build started |
| DRONE_BUILD_CREATED | build created |
| DRONE_TAG | build tag |
| DRONE_JOB_STARTED | job started |
