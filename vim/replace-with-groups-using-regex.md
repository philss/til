# Replace with groups using Regex in Vim

This is a very useful way to replace data. I keep forgeting what should be scape, so
this should help me in the future.

Suppose you want to replace a Github handler to the complete link:

```
@philss
```

Should become:

```markdown
[@philss](https://github.com/philss)
```

You will need to "copy" the existent handle name and apply to two different places in the target
string.

The regex will looks like:

```
@\([A-Za-z0-9]*\)
```

Note that you need to scape the parentesis.

And the replacement part will be:

```
[@\1](https:\/\/github.com\/\1)
```

Basically what happens is that we are creating a group in the regex that will generate the `\1`
content with that group result (what is between parentesis).
We have to scape the slashes because vim will not understand which one is the delimiter of the
replace command.

In the end, it will looks like:

```
%s/@\([A-Za-z0-9]*\)/[@\1](https:\/\/github.com\/\1)/gc
```

