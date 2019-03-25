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
    CF_USER = "janedoe"
    CF_ORG = "it-department"
    CF_SPACE = "dev"
    EXTRA_ARGS = ""
  }
  secrets = ["CF_PASSWORD"]
}
```
