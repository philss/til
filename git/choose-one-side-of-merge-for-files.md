# Choose one side of merge for files

When merging, sometimes we need to choose one side for an entire file (like bundle files).
This can be performed by `git checkout`:

```
$ git checout --theirs -- path/of/files
```

or

```
$ git checkout --ours -- path/of/files
```

Be aware that you need to add the files with `git add` to mark the merge resolution.

Source: http://stackoverflow.com/a/16826016/1055602
