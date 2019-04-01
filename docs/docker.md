# Dockerfiles

Our analyzers are deployed as docker images.

- Your dockerfile should live at the root directory of your repository and it should be called `Dockerfile`
- Your dockerfile should be be the minimal needed for your analyzer and create the minimal image needed for analysis. It should use alpine linux if possible.
- The working directory should be `/opt/analyzer` (ie, we call `/opt/analyzer/bin/analyze.sh`)
- All changes to dockerfiles require a PR review from the core team.
