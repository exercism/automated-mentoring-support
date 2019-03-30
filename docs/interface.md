# The Interface

All interactions with the Exercism website are handled automatically. Analyzers have the single responsibility of taking a solution and returning a status and any messages.

## Execution

- An analyzer should provide an executable script at `bin/analyze.sh` which will be called by the external orchestrator. You can see [an example here](https://github.com/exercism/ruby-analyzer/blob/master/bin/analyze.sh#L4).
- The script will receive two parameters:
  - The slug of the exercise (e.g. `two-fer`).
  - A path to a directory containing the submitted file(s) (with a trailing slash).
- The script must write a file to that directory named `analysis.json`

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
      "comment": "ruby.general.some_paramaterised_message"
    },
    "ruby.general.some_paramaterised_message"
  ]
}
```

The following statuses are valid:
- `approve_as_optimal`: To be used when a solution matches pre-known optimal solutions.
- `approve_with_comment`: To be used when a solution can be approved but with a known improvement.
- `disapprove_with_comment`: To be used when a solution can be disapproved as suboptimal and a comment is provided.
- `refer_to_mentor`: This is the default situation and should be used when there is any uncertainty.

## Debugging

The contents of stdout and stderr from each run will be persisted into files that can be viewed later.

You may write an `analysis.out` file that contains debugging information you want to later view.

At a later date, we will provide an interface for you to download these files along with the submitted files and analysis.json.

## Comments

Exercism is responsible for the display and communication of comments. The analyzer's job is purely to provide functional comments. Please follow these guidelines:
- Comments should be actionable. The user should understand the action they need to undertake.
- While friendly, they should not try and pretend to be a human and should not contain greetings, etc.
- The solution should not act like the start of a discussion.

- A good comment would be "You could improve this solution by doing XYZ".
- A bad comment would be "Hello. Have you thought about doing XYZ?".
