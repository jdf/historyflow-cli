# historyflow

historyflow draws the history of a document as a picture, using the _history
flow_ visualization invented by
[Fernanda Viégas](https://www.fernandaviegas.com/) and
[Martin Wattenberg](https://www.bewitched.com/). Each version is a vertical
line, as tall as the version is long and colored by who wrote each part; bands
join each passage to the same passage in the next version. You can see at a
glance who wrote what, when, and what became of it.

It reads the history of a file in a git repository or of a Wikipedia article,
and runs in your browser, either from the `historyflow` command or at
https://mrfeinberg.com/historyflow/.

## Using it

### The command

```sh
historyflow                        # the git repository you are in
historyflow path/to/repo           # another repository
historyflow src/main.rs            # a repository, opened on one file
historyflow https://en.wikipedia.org/wiki/Chocolate    # a Wikipedia article
historyflow saved.hflow            # a saved history
```

Each opens the viewer in your browser. For a repository, the viewer lists its
text files; choose one to see its history, in which every commit that touched
the file is a version.

With `-o`, the command saves the history to a file, which opens later without
git or the wiki:

```sh
historyflow src/main.rs -o main.hflow
historyflow https://en.wikipedia.org/wiki/Chocolate -o chocolate.hflow
```

| Option           | Meaning                                                    |
| ---------------- | ---------------------------------------------------------- |
| `-o FILE`        | Save the history to `FILE` instead of opening the viewer.  |
| `--revisions N`  | How many of an article's revisions to fetch (default 500). |
| `--contact WHO`  | Who to name to Wikipedia for this run (see below).         |
| `--first-parent` | Follow only the mainline of a git history.                 |
| `--port N`       | The port to serve the viewer on (default 8793).            |
| `--no-open`      | Print the viewer's address without opening a browser.      |

Wikipedia asks every tool to say how to reach the person running it. Tell
historyflow once, with an email address, a website, or your user name on a wiki:

```sh
git config --global historyflow.contact you@example.com
```

### The viewer

- **Wikipedia…** fetches an article's history, given its address. **Stop** ends
  a fetch early.
- **Open…** opens a saved history, as does dropping one on the page. **Save**
  saves the history on screen.
- Click or drag on the plot to pick a version and a place in it. The panel on
  the right shows that version's text, colored as in the plot. The left and
  right arrow keys step through versions.
- Scroll or pinch to zoom in time, and scroll sideways to pan.

| Menu        | Choices                                                          |
| ----------- | ---------------------------------------------------------------- |
| **color**   | By author, or by the age of the text.                            |
| **spacing** | Versions evenly spaced, or spaced by date.                       |
| **height**  | The plot's height is the longest version in view, or of all.     |
| **scale**   | Linear, or logarithmic, which keeps very long versions in check. |
| **compare** | Versions compared by lines, by words, or by sentences.           |

A link can name an article: `https://mrfeinberg.com/historyflow/?wiki=` followed
by the article's address.

## Installing it

With [Homebrew](https://brew.sh), on macOS or Linux:

```sh
brew install jdf/historyflow/historyflow
```

Or download the archive for your platform from the
[latest release](https://github.com/jdf/historyflow-cli/releases/latest), unpack
it, and put `historyflow` on your `PATH`. There are builds for macOS (Apple
silicon and Intel) and Linux (x86-64).

The command uses `git` to read a repository and `curl` to save an article.

## Credits

The history flow visualization was invented by
[Fernanda Viégas](https://www.fernandaviegas.com/) and
[Martin Wattenberg](https://www.bewitched.com/) at IBM Research in 2003, and
described by them and Kushal Dave in _Studying Cooperation and Conflict between
Authors with history flow Visualizations_ (CHI 2004).

This implementation is by Jonathan Feinberg, under the [MIT license](LICENSE).
The viewer's About box lists the licenses of the software it is built with.
