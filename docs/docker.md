# Dockerfiles

Our analyzers and representers are deployed as docker images.

- Your dockerfile should live at the root directory of your repository and it should be called `Dockerfile`.
- Your dockerfile should create the minimal image needed for your analyzer/representer.
  Applying the official [Dockerfile best practices](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/) can help to create a minimal image. The minimal-sized image is often based on Alpine Linux.
- All changes to dockerfiles require a PR review from the @exercism/ops.
- The docker image should include the [tooling-webserver](https://github.com/exercism/tooling-webserver/blob/master/README.md#installation-docker).

### Analyzers

- The working directory should be `/opt/analyzer`.
- There should be a `/opt/analyzer/bin/run.sh` script that can be called with 3 parameters: the `exercise slug`, the path to the `solution folder`, and the path to the `output folder`. For more information see [The Interface](./analyzers/interface.md).

### Representers

- The working directory should be `/opt/representer`.
- There should be a `/opt/representer/bin/run.sh` script that can be called with 3 parameters: the `exercise slug`, the path to the `solution folder`, and the path to the `output folder`. For more information see [The Interface](./representers/interface.md).

## Configuration

Configuration can be set in the [`tools.json` file](https://github.com/exercism/tooling-invoker/blob/main/tools.json) in the Tooling Invoker repository. 

### Network

Tools run without access to the internet. There are two different configurations you can use:
1. `none`. This disables the networking device inside the container.
2. `internal`. This adds a networking device inside the container but the network has no access to anything external.

Different languages perform better/worse with different configurations (e.g. Ruby is 2x faster with `none`. Elixir is `12x` faster with `internal`.

You can experiment locally by using the `--network` flag when running your docker. `--network none` is supported by default. 
To use the internal network, first run `docker network create --internal internal` to create the network, then use `--network internal` when running the container.

### Memory

Languages can set the maximum memory they need to use to run their jobs. Setting this to be as low as possible means that we can run more jobs more quickly in parallel. It also means that people who try and abuse memory will not be able to succeed. Different langauges need wildly different maximum memory usage. Benchmarking the execution of a docker run to establish the maximum memory it uses is advised and appreciated.

Memory [should be specified](https://docs.docker.com/config/containers/resource_constraints/#limit-a-containers-access-to-memory) using the number with suffix of b, k, m, g, to indicate bytes, kilobytes, megabytes, or gigabytes.

### Running Docker locally

You can test the settings above using this command:
```
docker container run -v /path/to/job:/mnt/exercism-iteration --network none -m 1GB exercism/ruby-test-runner lasagna /mnt/exercism-iteration/ /mnt/exercism-iteration/
```
