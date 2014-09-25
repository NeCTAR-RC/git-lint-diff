Git Lint Diff
=============

A tool to limit what lines of files checked so that you can gradually
reach a lint free repository.

Example usage::

 $ ./git-lint-diff -h
 usage: git-lint-diff [-h] [-v] [-a] [-r REVISION] --linter
                      {puppet-lint,flake8} [-g GIT_EXECUTABLE]
                      [ARG [ARG ...]]

 positional arguments:
   ARG                   The executable to run, and any desired arguments.
                         (default: None)

 optional arguments:
   -h, --help            show this help message and exit
   -v, --verbose         Increase verbosity (specify multiple times for more).
                         (default: 0)
   -a, --all             Check the entire repository, not just changed files.
                         (default: False)
   -r REVISION, --revision REVISION
                         A revision to compare against e.g. origin/master or
                         9ec079b. (default: df2ff0d76edfa4d81e7ca1b6cfbad6675b88042d)
   --linter {puppet-lint,flake8}
                         The linter to use. (default: None)
   -g GIT_EXECUTABLE, --git-executable GIT_EXECUTABLE
                         The executable to run. (default: /usr/bin/git)


The linter will only report lines changed in the most recent commit::

 $ ./git-lint-diff --linter flake8
 ./patchman/util/templatetags/common.py:168:31: E225 missing whitespace around operator

 ....Skipped 127 lines.....


Or any commit of your chooseing::

 $ ./git-lint-diff --linter flake8 -r origin/master
 ./patchman/util/templatetags/common.py:168:31: E225 missing whitespace around operator
 ./setup.py:98:12: E251 unexpected spaces around keyword / parameter equals
 ./setup.py:98:14: E251 unexpected spaces around keyword / parameter equals

 ....Skipped 124 lines.....
