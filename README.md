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

It can also show the history of a Wikipedia article, which your browser fetches
from the wiki, or fetch one into a compact history file to open later:

```sh
historyflow --wikipedia https://en.wikipedia.org/wiki/Chocolate
historyflow --wikipedia Chocolate --revisions 2000 -o chocolate.hflow
historyflow chocolate.hflow
```

It reads the first 500 revisions unless `--revisions` says otherwise. Wikipedia
asks every tool to say how to reach whoever is running it, so tell historyflow
once how to reach you (an email address, a website, or your user name on a
wiki); it is sent to the wiki with each request and nowhere else:

```sh
git config --global historyflow.contact you@example.com
```

## Install

With [Homebrew](https://brew.sh), on macOS or Linux:

```sh
brew install jdf/historyflow/historyflow
```

Or download the archive for your platform from the
[latest release](https://github.com/jdf/historyflow-cli/releases/latest), unpack
it, and put `historyflow` somewhere on your `PATH`. There are builds for macOS
(Apple silicon and Intel) and for Linux on x86-64.

It needs `git` to read a repository's history, a web browser, and `curl` for
`--wikipedia` with `-o`.

## This repository

Releases of the program are published here, by `.github/workflows/release.yml`.
The Homebrew formula is in
[jdf/homebrew-historyflow](https://github.com/jdf/homebrew-historyflow).
