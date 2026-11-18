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

## Install

No release has been published yet; these instructions take effect with the
first one.

With [Homebrew](https://brew.sh), on macOS or Linux:

```sh
brew tap jdf/historyflow-cli https://github.com/jdf/historyflow-cli
brew install historyflow
```

Or download the archive for your platform from the
[latest release](https://github.com/jdf/historyflow-cli/releases/latest), unpack
it, and put `historyflow` somewhere on your `PATH`. There are builds for macOS
(Apple silicon and Intel) and for Linux on x86-64.

It needs `git` to read a repository's history, and a web browser.

## This repository

Releases of the program are published here, along with the Homebrew formula
(`Formula/historyflow.rb`). Both are produced by `.github/workflows/release.yml`.
