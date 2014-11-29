# shellapp

Turn a shell script into an OS X application.

## Usage

    shellapp example.sh example.app

## Description

Creates an OS X application bundle that calls a given shell script or
command.

This provides a command line alternative to creating application bundles with
Automator. The shell script is first wrapped in a short AppleScript
wrapper which is then compiled with `osacompile`. When the output file
includes the .app extension, `osacompile` outputs an application bundle
wrapping the AppleScript file.

### Example Use Case

Homebrew installs applications to `/usr/local`, which is not indexed by
Spotlight. The `brew linkapps` command creates symbolic links in
`/Applications` (or `~/Applications` when passed the `--local` flag),
but Spotlight doesn't index symbolic links.

In order to create an application bundle that is indexed by Spotlight
and that opens an instance of MacVim installed with Homebrew, we can use
the following command:

    shellapp "open /usr/local/Cellar/macvim/7.4-73_1/MacVim.app" /Applications/MacVim.app

`MacVim.app` can now be used to open the homebrew-install MacVim.

## Similar Tools

- https://gist.github.com/mathiasbynens/674099
  - Creates very simple applications, but they are too simple to be
    recognized by Spotlight as applications.
- http://www.sveinbjorn.org/platypus
