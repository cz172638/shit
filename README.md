# shit

shit == Shell Git

This is an implementation of Git using (almost) entirely POSIX shell.

Caveats:

- There are a couple of GNU coreutilsisms, which are marked with "XXX: GNUism"
  throughout. They have been tested on BusyBox as well.
- A native zlib implementation is required: [zlib](https://github.com/kevin-cantwell/zlib)
- Why the fuck would you use this

## Status

Enough plumbing commands are written to make this write the initial commit with
itself, which is how the initial commit was written. Huzzah.

## How to use

1. Don't

Okay, fine. Because only plumbing commands are implemented, you have to live
with a garbage manual process. Do something like this:

```
git clone https://git.sr.ht/~sircmpwn/shit
mkdir my-project
cd my-project
../shit/init
# Write some code
```

So we'll assume shit is at `../shit`.

To create a new index from all of your files (note, subdirectories aren't
working yet):

```
../shit/update-index *
```

Then to create a tree object from these:

```
../shit/write-tree | ./hash-object -t tree -w
```

This will print the tree ID to stdout. Use that to make a commit:

```
export GIT_AUTHOR_NAME="Your Name"
export GIT_AUTHOR_EMAIL="you@example.org"
../shit/commit-tree <tree sha> | ./hash-object -t commit -w
```

This will print out the new commit's SHA. To update master to point to this new
commit:

```
echo <commit sha> > .git/refs/heads/master
```

Tada.
