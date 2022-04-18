# Resource origin example repository

The EngineMQ broker is able to work in a gitops way. In this case, it updates its resources from a github repository: auths, routers and validiators.

This repo is a public example of how to build such a repo. You can use a dedicated repo, all of whose files are loaded into the broker. Or you can use monorepo and each broker can have their own directory.

All yaml files are processed by recursively traversing the folders. When you use the .yamlignore file, you can exclude certain files temporarily or permanently.

## Usage with ENV variable

You can set the environment variable to automatically update resources from a remote repo:
```
RESOURCE_ORIGIN=github(repo=EngineMQ/resource-sample token=ghp_???? branch=master folder=/)
```
- token: optional parameter if you are using a private repo.
- branch: optional parameter if you are not using the default branch.
- folder: optional parameter if you do not want to process files from the root directory.

## Usage with helm chart

You can set the remote repo in the https://github.com/EngineMQ/helm-broker repo **values.yaml** file, which returns the above ENV variable.
```
resourceOrigin:
  repo: EngineMQ/resource-sample
  token: ghp_?????
  branch: master
  folder: /
```
