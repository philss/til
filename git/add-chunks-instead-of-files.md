# Add chunks instead of files

One trick I learned with [Sergio Nogueira](https://github.com/scnfilho) is that you can add
chunks of files instead of the complete files in git.

This can be done with `git add -p`. The command will ask you if you want to add, skip, split more or
cancel a giving chunk of file. It is interactive and will add things to the staging area, ready to
be commited.

## Gotchas

I couldn't make it work with untracked files. So you need to at least
add the file in the staging area before use `git add -p` for the first time.

## Futher usage

You can use the same technique with `git reset --patch` to reset portions of files, and with
`git stash save --patch` to save parts of files into the stash area.
