## Git exercise: Advanced interactive rebase
You have worked on a new feature called Hello World.
This features ends up being complete with both documentation and unit test, but there are a few problems.
The history looks really messy, with lots of small half-finished steps, and there are things included that should never have been there.

You should fix this such that your `git log` looks great!

To do this we will use our good friend `git rebase --interactive`

Luckily we have a release tag `v0.0` from just before we started the feature.

As this is an advanced exercise, there are no specific steps to follow and no single solution.

## Setup:

```sh
git commit --allow-empty -m "Initial commit"

git tag v0.0

git push origin master
git push origin v0.0

echo "Hello" > hello.code
git add hello.code
git commit -m "Helo Volrd feature"


echo "HelloWrld?" > hello.code
echo "Unrelated stuff!" > other.code
git add -A
git commit -am "Finished HW feature"

echo "Hello World!" > hello.code
git commit -am "Really made the thingy done"

echo "println DEBUG" >> hello.code
git commit -am "debugging"

echo "4321pass" > private.secret
git add private.secret
git commit -m "important secret"

echo "# THE Hello World program" > README.md
git add README.md
git commit -m "Add doc - step 1"

echo "# THE Ultimate Hello World program" > README.md
git commit -am "Add doc - step 2"

echo "" >> README.md
echo "This program does exactly what it says" >> README.md
git commit -am "Add doc - step 3"

echo "does_it_work(hello.code)" > hello.test
git add hello.test
git commit -m "Test for feature hello world"

echo "does_it_work(hello.code);" > hello.test
git commit -am "I forgot a semicolon"
```

## Task

1. Explore the repo and the history so you know what happened
2. Use `git rebase --interactive v0.0` to let you edit the "recipe" for the entire feature development.
3. Clean up the history such that it actually makes sense. Try to use as many of the rebase "features" (e.g. reword, squash, fixup, drop) as possible. You decide yourself if you want to rewrite the whole thing in one go, or apply a few changes first, then run a new `git rebase --interactive v0.0` to keep cleaning.

### useful commands

- `ls -l`                 # list files
- `tail -n +1 *`          # show content of all files
- `git log --oneline`     # show history
- `git log --stat`        # log which files changed
- `git log --patch`       # log with diff
- `git rebase -i <ref>`   # run the interactive rebase back to <ref>
