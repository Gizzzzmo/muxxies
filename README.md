# Muxxies

A few shell utilities to improve working with tmux.

## Envmux

Creates a new tmux session in the current working directory, and attaches to it.

- Name of the directory becomes the title of the session
- If already in a session, it switches to the newly created session instead of
  trying to nest.
- It puts all environment variables of the calling shell into tmux's
  environment, meaning all future windows in that session will also inherit that
  environment

Todo:

- [ ] fix a bug in the flake.nix packaged version that introduces an extra
  directory into tmux's PATH variable.

## Sourcemux

Sets the environment variables of the current tmux session to those of the
current process. Useful when already in a session, and maybe you want to
activate a python virtual environment or something. Just source the environment,
and then do `sourcemux`. All new windows in that session will now inherit that
environment.

**Careful** Processes in existing windows do not have their environment
modified.

Todo:

- [ ] same bug as with `envmux`

## Multimux

`multimux <dir1> <dir2> ...`

Creates a new window in the current session. In that window a pane is opened for
every directory supplied as an argument, changing to the directory in that pane.
The panes are then synchronized, meaning every keystroke goes to all panes.

If no arguments are supplied, then all non-hidden subdirectories of the current
working directory are used instead.
