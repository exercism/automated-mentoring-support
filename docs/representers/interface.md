# The Interface

All interactions with the Exercism website are handled automatically. Representers have the single responsibility of taking a solution and returning a representation of it.

A _representation_ is an extraction of the solution to its essence without names, comments, spacing, etc. but still uniquely identifying the approach taken. Two different ways of solving the exercise must not have the same representation.

## Execution

- A Representer should provide an executable script. You can find more information in the [docker.md](https://github.com/exercism/automated-mentoring-support/blob/master/docs/docker.md) file.
- The script will receive two parameters:
  - The slug of the exercise (e.g. `two-fer`).
  - A path to a directory containing the submitted file(s) (with a trailing slash).
- The script must write a file to that directory named `representation.txt`

## Output format

The `representation.txt` file contain some sort of canconical representation (normally an AST)

## Debugging

The contents of `stdout` and `stderr` from each run will be persisted into files that can be viewed later.

You may write an `representation.out` file that contains debugging information you want to later view.

At a later date, we will provide an interface for you to download these files along with the submitted files and `representation.txt`.
