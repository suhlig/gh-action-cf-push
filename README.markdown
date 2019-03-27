# `cf push` Action

A GitHub action that pushes the source code to a Cloud Foundry instance.

# Example

```
workflow "cf push on git push" {
  on = "push"
  resolves = "push to CF"
}

action "push to CF" {
  uses = "suhlig/gh-action-cf-push@master"
  env = {
    API_ENDPOINT = "api.example.com"
    CF_ORG = "it-department"
    CF_SPACE = "dev"
    EXTRA_ARGS = ""
  }
  secrets = ["CF_USERNAME", "CF_PASSWORD"]
}
```

# Test

```command
# build the image
docker build . -t suhlig/cf-push

# set the variables
export GITHUB_WORKSPACE=.
export API_ENDPOINT=api.example.com
export CF_USERNAME=janedoe
export CF_PASSWORD=********
export CF_ORG=it-department
export CF_SPACE=dev

# launch the container
docker run \
    --interactive \
    --tty \
    --rm \
    --env GITHUB_WORKSPACE \
    --env API_ENDPOINT \
    --env CF_USERNAME \
    --env CF_PASSWORD \
    --env CF_ORG \
    --env CF_SPACE \
  suhlig/cf-push
```
