# The Interface

All interactions with the Exercism website are handled automatically. Analyzers have the single responsibility of taking a solution and returning a status and any messages.

## Execution

- An analyzer should provide an executable script. You can find more information in the [docker.md](../docker.md) file.
- The script will receive three parameters:
  - The slug of the exercise (e.g. `two-fer`).
  - A path to a directory containing the submitted file(s) (with a trailing slash).
  - A path to an output directory (with a trailing slash). This directory is writable.
- The script must write an `analysis.json` file to the output directory.

## Output format

The `analysis.json` file should be structured as followed:

```json
{
  "status": "...",
  "comments": [
    {
      "comment": "ruby.general.some_paramaterised_message",
      "params": { "foo": "param1", "bar": "param2" }
    },
    {
      "comment": "ruby.general.some_paramaterised_message",
      "params": {}
    },
    {
      "comment": "ruby.general.some_paramaterised_message"
    },
    "ruby.general.some_paramaterised_message"
  ]
}
```

Messages are keys into `website-copy/automated-comments/`, e.g. [`ruby.general.explicit_return -> automated-comments/ruby/general/explicit_return.md`](https://github.com/exercism/website-copy/blob/47af5b309ac263629ca5c52904046f81e0cc8def/automated-comments/ruby/general/explicit_return.md).
Those markdown files can be parameterized with strings like this `Try %{variable_name} += 1 instead`.

The following statuses are valid:

- `approve`: To be used when a solution can be approved.
- `disapprove`: To be used when a solution can be disapproved as suboptimal and a comment is provided.
- `refer_to_mentor`: This is the default situation and should be used when there is any uncertainty.

## Debugging

The contents of `stdout` and `stderr` from each run will be persisted into files that can be viewed later.

You may write an `analysis.out` file that contains debugging information you want to later view.

At a later date, we will provide an interface for you to download these files along with the submitted files and `analysis.json`.

## Comments

Exercism is responsible for the display and communication of comments. The analyzer's job is purely to provide functional comments. Please follow these guidelines:

- Comments should be actionable. The user should understand the action they need to undertake.
- While friendly, they should not try and pretend to be a human and should not contain greetings, etc.
- The solution should not act like the start of a discussion.

- A good comment would be "This solution may be improved by doing XYZ".
- A bad comment would be "Hello. Have you thought about doing XYZ?".
