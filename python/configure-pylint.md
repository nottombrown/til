# Configure Pylint

Linting is awesome. It catches errors faster and keeps your code fresh. If you're using atom, you can get notifications on each line whenever you save with [linter-pylint](https://atom.io/packages/linter-pylint).

When you're starting a new project, generate a new linter with the following:

```bash
pylint --generate-rcfile > pylintrc
```

Then, if there are errors that you don't need, can disable them in the `disable` section under `[MESSAGES CONTROL]`

I also use 2-space indenting. You can change that in the `indent-string` setting.
