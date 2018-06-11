# git-idm v0.6

New features:

- Warn user when using a version of `git` older than 2.10.
- New option `--ssh-command` which can be specified to use a completely custom
  SSH command rather than relying on the default provided by `--key`.

# git-idm v0.5

New features:

- Warn user about private key not being added to `ssh-agent` when using the `git
  idm use` command.

# git-idm v0.4

Bugfixes:

- Active identity misprinting multiple IDs.

# git-idm v0.3

New features:

- Add `-v` and `--version` options in addition to `git idm version`.

Bugfixes:

- shellcheck recommendations

# git-idm v0.2

New features:

- Added short commands `git idm rm` and `git idm ls` for `remove` and `list`
  respectively.

Bugfixes:

- Avoid removing an empty identity.
- Document `git idm version`.

# git-idm v0.1 (initial release)

Released with commands:

```
git idm active
git idm add
git idm list
git idm remove
git idm uninstall
git idm use
git idm version
```
