# Contributing:

## Feature requests:
If you have a feature request open an issue and use the `enhancement` label. Make sure you describe the feature you want in sufficient detail

## Issues:
If you find an issue then firstly search to see if it has already been reported. If not then open a new issue with the label `bug`. Make sure you include details of:
- The events leading to the issue
- What the issue is/how it manifests
- The PAM logs relating to the issue

Try to give the "minimum" example to reproduce the bug where possible

## Pull requests:
When opening a pull request:
- Open a draft PR when you start working. This allows others to see you are working on a bug/feature and avoids duplicate work
- Ensure your code meets the coding conventions listed below
- Try to stick to 1 feature/bug per PR
- Include details of what your changes do, for example what feature you implement or which bug you fix

## Code Conventions:
- Use 4 spaces for tabs
- Include type signatures for all top level functions
- Include Haddock comments for all functions/type definitions, as well as inline comments explaining logic where it may not be clear
- Try to avoid long lines - if a line is looking long then split it across 2 lines, or use `let...in...` or `...where` if it makes your code more readable
- Update the README with new features or changes to existing ones
