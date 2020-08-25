# Dockerfiles

Our analyzers and representers are deployed as docker images.

- Your dockerfile should live at the root directory of your repository and it should be called `Dockerfile`.
- Your dockerfile should create the minimal image needed for your analyzer/representer.
  It should use alpine linux if possible. Applying the official [Dockerfile best practices](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/) can help to create a minimal image.
- All changes to dockerfiles require a PR review from the @exercism/ops.
- The docker image should include the [local-tooling-webserver](https://github.com/exercism/local-tooling-webserver/blob/master/README.md#installation-docker).

### Analyzers
- The working directory should be `/opt/analyzer`.
- There should be a `/opt/analyzer/bin/run.sh` script that can be called with 3 parameters: the `exercise slug`, the path to the `solution folder`, and the path to the `output folder`. For more information see [The Interface](./analyzers/interface.md).

### Representers
- The working directory should be `/opt/representer`.
- There should be a `/opt/representer/bin/run.sh` script that can be called with 3 parameters: the `exercise slug`, the path to the `solution folder`, and the path to the `output folder`. For more information see [The Interface](./representers/interface.md).

More background information and optional hints:
- To run the containers in production the `runc` command is used which does not use the `ENTRYPOINT` specified in the `Dockerfile`. It would still be good to have an `ENTRYPOINT` specified for local use and testing.
- The students solution is currently mounted to `/mnt/exercism-iteration/` in production. We still pass in the solution folder as the second argument to the analyzer in case that changes in the future.
