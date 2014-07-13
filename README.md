# manuel-contrib-watch

A plugin for [manuel](https://github.com/ShaneKilkelly/manuel), which
watches for changes in a directory and reacts with user-defined actions


# Prerequisites

This plugin depends on the `inotify-tools` package for linux, specifically
the `inotifywait` program.


# Installation

Clone this repository into your manuel plugins
directory ($HOME/.manuel.d/plugins by default):
```bash
$ cd ~/.manuel.d/plugins
$ git clone git://github.com/ShaneKilkelly/manuel-contrib-watch.git
```


# Usage

Start the `manuel_watch` task, providing a directory to watch over, and an
associative-array of file-patterns to watch for and corresponding actions
to take when a file matchin that pattern changes.

Example:
```bash
# In a manuelfile

load_plugin manuel-contrib-watch

function do_something {
  declare -A actions=(
    ["\.js$"]="echo 'we should concat and minify the js again'"
    ["\.go$"]="go build ."
  )

  manuel_watch . actions
}
```
