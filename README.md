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
