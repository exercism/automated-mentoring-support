# Dockerfiles

Our analyzers are deployed as docker images.

- Your dockerfile should live at the root directory of your repository and it should be called `Dockerfile`
- Your dockerfile should be be the minimal needed for your analyzer and create the minimal image needed for analysis. It should use alpine linux if possible.
- The working directory should be `/opt/analyzer`
- There should be a `/opt/analyzer/bin/analyze.sh` script that can be called with 2 parameters: the `exercise slug` and the `solution folder`. For more information see [The Interface](https://github.com/exercism/automated-mentoring-support/blob/master/docs/interface.md).
- All changes to dockerfiles require a PR review from the @exercism/ops.

More background information and optional hints:
- To run the containers in production the `runc` command is used which does not use the `ENTRYPOINT` specified in the `Dockerfile`. It would still be good to have an `ENTRYPOINT` specified for local use and testing.
- The students solution is currently mounted to `/mnt/exercism-iteration/` in production. We still pass in the folder as a second argument to the analyzer in case that changes in the future.
