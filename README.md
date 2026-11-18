# historyflow

`historyflow` is a command-line program that shows how a document came to be,
version by version: who wrote what, and what became of it. It is a
reimplementation of Fernanda Viégas and Martin Wattenberg's _history flow_
visualization (IBM Research, 2003).

Run it in a git repository and it opens your browser on a viewer for the history
of any file there. The viewer is part of the program and is served from your own
machine; nothing is fetched from anywhere else.

```sh
historyflow                 # browse the git repository you are in
historyflow src/main.rs     # open one file's history
historyflow saved.hflow     # open a saved history file
```

This repository is where releases of the program are published. There are none
yet.
