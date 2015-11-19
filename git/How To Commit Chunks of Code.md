OMFG!

I've always wondered wether it existed or not. The answer is: it does exist!

We can include into a commit picked pieces of code that lives in a file with a
bunch of modifications that we don't want to include. It's pretty simple to do:

    $ git add file_with_modifications.any -p

Git will display a helpful and interactive utility that allows us to choose which
pieces of code to include in our changes to commit.

It's worth noting that we may choose the `s` option if some chunk of modification
is too large. Git will then split it out.

What if we want to discard a few lines of code in the same fashion? `git checkout`
also supports the `-p` option!

    $ git checkout file_with_mods.any -p

The `-p` option stands for patch. We may fetch the details with commands like
this:

    $ git checkout --help

```
-p, --patch
   Interactively select hunks in the difference between the <tree-ish> (or the index, if unspecified) and the working tree. The chosen hunks are then applied in reverse to the working tree (and if a <tree-ish> was specified,
   the index).

   This means that you can use git checkout -p to selectively discard edits from your current working tree. See the “Interactive Mode” section of git-add(1) to learn how to operate the --patch mode.
```
