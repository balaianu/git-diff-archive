# git-diff-archive

Git plugin for exporting the changed files between the current HEAD and an older commit as an archive.

---

It's useful for projects where you need to package updates to an existing codebase, but for some reason there is no CI/CD or GIT available on the destination server.

It's for those times when you still want to have a git-based workflow for development, and not have to hunt inside your project for files that need to be updated (mostly for legacy projects or clients with limited infrastructure - at least in my use case).

The plugin will find all files that have changes between your project's HEAD and an older commit and package them nicely inside an archive - *except deleted files, you don't neet those anyway :)*

You can then extract the archive on your destination server, inside the root folder of your project, and just overwrite the files contained in your archive.

**Disclamer**: I know, I know, this is bad practice, just upgrade your workflow, upgrade your infrastructure, upgrade your clients etc... But we all know sometimes you just gotta make do with what you have :)

**NOTE**: all archives created will have the current timestamp appended to the filename.

## How to Install

1. Download or clone the current repository.
2. `cd git-diff-archive`
3. `make install`

**NOTE**: The plugin executable will be install in `~/bin`, so it will only be available to the current user (*for now*).

## How to Uninstall

1. `cd /path/to/git-diff-archive` (the one you downloaded earlier, or a fresh copy)
2. `make uninstall`

## How to use it

Open a terminal and navigate to your git project's working directory, then use as you would any other git command:

`git diff-archive [<options>] [<commit>]`

#### Available options:

<table>
<tr>
<td>-d, --destination</td>
<td>Path to folder in which tp save the archive</td>
</tr>
<tr>
<td>-n, --name</td>
<td>Name of the exported archive (without extension)</td>
</tr>
<tr>
<td>-f, --format</td>
<td>Archive format (tar or zip - default: zip)</td>
</tr>
<tr>
<td>-s, --stamp</td>
<td>Append revision info to the archive's file name</td>
</tr>
<tr>
<td>-v, --version</td>
<td>Display current plugin version</td>
</tr>
<tr>
<td>-h, --help</td>
<td>Display information about usage in the terminal</td>
</tr>
</table>

#### Examples

`git diff-archive 702b3f` - Will generate an archive with the changed files between `HEAD` and the commit with the short hash id of `702b3f`

`git diff-archive v1.0.0` - Will generate an archive with the changed files between `HEAD` and the commit tagged with `v1.0.0`

`git diff-archive -h` - Will display usage information

`git diff-archive -v` - Will display the current plugin version

`git diff-archive --format tar` - Will generate a `.tar` archive

`git diff-archive -n my_archived_changes` - Will generate an archive named `my_archived_changes.zip`

`git diff-archive --stamp` - Will add the short hashes of the 2 commits in use in the archive file name

`git diff-archive -d /home/myuser/archives` - This will create the archive file in the folder `/home/myuser/archives`

## Issues and Features

Please submit any issues, bugs and/or feature requests with as much information about it as possible.

This is something I built for personal use, but I will try to fix any bugs you find if time allows it.

## Contributing

Contributions are absolutely welcome. Ideally submit a pull request, with the following notes:

- **Bug Fixes** - submit a pull request against the `master` branch.
- **Enhancements / New Features** - submit a pull request against the `develop` branch.

