# Check commit message with git hooks

Add a prepare-commit-msg file  in .git/hooks directory to support/enforce [Conventional Commits naming convention](https://www.conventionalcommits.org/en/v1.0.0/).

```sh
#!/bin/bash

MESSAGE=$(cat $1) 
COMMITFORMAT="^(feat|fix|docs|style|refactor|test|chore|perf|other)(\((.*)\))?: (.*)$"

if ! [[ "$MESSAGE" =~ $COMMITFORMAT ]]; then
  echo "Your commit was rejected due to the commit message. Skipping..." 
  echo ""
  echo "Please use the following format:"
  echo "feat: feature example comment"
  echo "fix(ui): bugfix example comment"
  echo ""
  echo "(feat|fix|docs|style|refactor|test|chore|perf|other)"
  echo "More details on https://www.conventionalcommits.org/en/v1.0.0/"
  exit 1
fi
```