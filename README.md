# aur-repo 1.0.0

This Script is written for ArchLinux systems which provide a repository
solely containing software from the AUR. The task is to maintain a given
set of packages from the AUR and keep them up to date in the local repo.

Please see the [man page][man] for detailed information about `aur-repo`.

## Usage

```
Usage: aur-repo [-hnqv] [command]

  -h : Show this help and exit.
  -n : Dry run. Show executed commands but don't run them.
  -q : Be quiet. Do not print any message (but log them to the logfile).
  -v : Show version.

Commands:
  update                    Update the whole repository.
  update package            Force update of the specified package
  add package [mode]        Add new package to the list, 'mode' is the same as
                            in the config file and defaults to 'm'.
  addbuild package [mode]   Same as above plus building the package right away.
  remove package            Remove package from repository and delete all source files.
  info                      Show some info about the repository.
  list                      List all current packages in the repository database.

Config file example:

  REPONAME=my-repo
  GET_FROM_AUR=(
    package1=a
    package2=m
    package3=n
  )

Options:
a ... build always a new package
m ... only build a new package if the PKGBUILD in AUR changed
n ... ignore package (useful if the package at AUR is currently broken)
```
## License

Copyright (c) 2011 Jan-Erik Rediger <http://fnordig.de/about/>

Permission  is  hereby granted, free of charge, to any person ob-
taining a copy of  this  software  and  associated  documentation
files  (the "Software"), to deal in the Software without restric-
tion, including without limitation the rights to use, copy, modi-
fy, merge, publish, distribute, sublicense, and/or sell copies of
the Software, and to permit persons to whom the Software is  fur-
nished to do so, subject to the following conditions:

The  above  copyright  notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF  ANY  KIND,
EXPRESS  OR  IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES
OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE  AND  NONIN-
FRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE
LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER  IN  AN
ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN
CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN  THE
SOFTWARE.

[man]: http://badboy.github.com/aur-repo
