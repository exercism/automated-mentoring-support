# Automated Analysis on Exercism

Exercism' Automated Analysis a long-term endeavour to provide rapid feedback to students through the use of automated code analysis.

There are two elements to analysis:
- **Analyzers:** Using syntax analysis to work out the correct feedback to give. Analyzers are pretty complex and challenging endeavours.
- **Representers:** Creating generalised representations from the syntax tree of a submission, in order for us to later match similar code. Representers are pretty straight-forward to build.

The deployment and execution of both Analyzers and Representers is all handled by the Exercism Ops team.

We welcome contributions to both Analyzers and Representers

## Analyzers

If you would like to get involved in helping with [an existing Analyzer, please open an issue in its repository](https://github.com/exercism?q=analyzer) asking if there is somewhere you can help.

If you would like to create an analyzer for a different language, please follow the [these instructions](./docs/analyzers/getting-started.md).

## Representers

If you would like to get involved in helping with [an existing Representer, please open an issue in its repository](https://github.com/exercism?q=representer) asking if there is somewhere you can help.

If you would like to create a Representer for a different language, please follow the [these instructions](./docs/representers/getting-started.md).

## Background

The project started in February 2019 with support from Mozilla. For more information, we recommend reading [our announcement](https://exercism.io/blog/automated-mentoring-support-project) or this repository's [about document](./docs/about.md).

## Copyright

All content in this repository is Copyright to Exercism and licenced under MIT.

