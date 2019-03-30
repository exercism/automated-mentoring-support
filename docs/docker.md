# Dockerfiles

Our analyzers are deployed as docker images.

- Your dockerfile should live at the apex of your repository and it should be called `Dockerfile`
- Your dockerfile should be be the minimal needed for your analyzer and create the minimal image needed for analysis. It should use alpine linux if possible.
- The working directory should be `/opt/analyzer` and an `ENTRYPOINT` should define the script to execute with the given parameters (e.g. `ENTRYPOINT ["/opt/analyzer/analyzer.sh"]`.
- The students solution will be mapped to the folder `/solution` inside the docker container.
- All changes to dockerfiles require a PR review from the core team.
