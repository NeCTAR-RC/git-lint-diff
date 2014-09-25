Git Lint Diff
=============

A tool to limit what lines of files checked so that you can gradually
reach a lint free repository.

Example usage::

 $ ./git-lint-diff
 usage: git-lint-diff [-h] [-v] [-a] [--linter {puppet-lint,flake8}]
                      [-g GIT_EXECUTABLE]
                      ARG [ARG ...]

 positional arguments:
   ARG                   The executable to run, and any desired arguments.

 optional arguments:
   -h, --help            show this help message and exit
   -v, --verbose         Increase verbosity (specify multiple times for more).
                         (default: 0)
   -a, --all             Check the entire repository, not just changed files.
                         (default: False)
   --linter {puppet-lint,flake8}
   -g GIT_EXECUTABLE, --git-executable GIT_EXECUTABLE
                         The executable to run. (default: /usr/bin/git)

