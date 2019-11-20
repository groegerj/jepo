# jepo

Copyright (C) 2019 Josua Groeger.

jepo is a tool built on top of git that helps manage many git repositories.
It is meant to be an alternative to Google repo.

# LICENSE

LNL is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

LNL is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with LNL.  If not, see <http://www.gnu.org/licenses/>.

# PURPOSE AND HISTORY

jepo was written to be a nearly drop-in replacement of repo.

https://gerrit.googlesource.com/git-repo

"Repo is a tool built on top of Git. Repo helps manage many Git repositories,
does the uploads to revision control systems, and automates parts of the development workflow.
Repo is not meant to replace Git, only to make it easier to work with Git.
The repo command is an executable Python script that you can put anywhere in your path."

This description applies to jepo as well, even though jepo is a Bash script.
The motivation for writing jepo was as follows.

* repo seems to expect the manifest to be used to be in a git repository on some server,
  whereas jepo works with local data.
* repo stores the project git repositories in some hidden subdirectory and creates,
  for the "visible" project directories, only the checked out data plus some weird links,
  whereas, with jepo, a project directory coincides with the git repository directory.
* jepo supports hook scripts, for which useful functions are provided.

# USAGE

/path/to/jepo /path/to/manifest.xml

* manifest.xml should be the main manifest, e.g. default.xml from the LineageOS
  android main repository https://github.com/LineageOS/android
* local manifests as with repo do not work, instead add a line such as
  <include name="local_manifest.xml" />
  near the end (but inside the <manifest> area) of the manifest.xml / default.xml.
* paths such as ".." relative to some server location in a remote do not work, e.g.

  <remote  name="github"
           fetch=".."
           review="review.lineageos.org" />

  must be replaced by

  <remote  name="github"
           fetch="https://github.com"
           review="review.lineageos.org" />

# STATUS

jepo has been tested successfully and seems to work as intended
(but not yet completely documented).
