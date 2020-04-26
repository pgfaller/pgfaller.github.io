Run a command in a clean environment

A "clean" `bash` environment may be had with
```
$ env -i bash --noprofile --norc <command>
```
- The `env -i` command executes the command given to it on the command line without transferring any of the exported environment variables of the old shell environment to the environment of the executed program.
- The `--noprofile` option stops `bash` from reading the system-wide or personal shell initialization scripts that would otherwise be read for a login shell.
- The `--norc` option stops `bash` from reading the personal shell initialization scripts that would otherwise be read for an interactive shell.