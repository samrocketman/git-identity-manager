# git-idm v0.10

Important Notes:

- Global settings will automatically be removed.
- If using an older version of Git such as git version 2.25.1 on Ubuntu 20.04
  then there's no need to upgrade.

Bug fixes:

- Bugfix tracked directories is broken for git version 2.38.1.

# git-idm v0.9

Important Notes:

- The bugfix for active identity includes a backwards compatible config
  migration.  This config migration code will be removed after 5 or 6 releases
  from now since it will likely no longer be required.

Bug fixes:

- Show proper active identity within a tracked directory.  Before, it would only
  show the global identity and didn't properly sanity check the identity.

New features:

- New command `git idm copy-key-to` which copies SSH keys from other identities
  into the specified identity.  This command is more for migration purposes.

# git-idm v0.8

New features:

- GPG commit signing now supported per identity.  See pull request [#4][#4] and
  [#5][#5].

[#4]: https://github.com/samrocketman/git-identity-manager/pull/4
[#5]: https://github.com/samrocketman/git-identity-manager/pull/5

# git-idm v0.7

Important Notes:

- When using `git idm track` to configure identity directory tracking,
  configuration files are now created separately from your git config.  The
  configuration files are named `~/.gitconfig_idm_<identity>`.
- Due to the new feature identity directory tracking, identity names now must be
  a limited set of characters.  Only uppercase, lowercase, underscore, and
  hyphen are valid characters in an identity name.
- Minimum recommended git version is raised from 2.10 to 2.13.  This is to
  support the new feature identity directory tracking.

New features:

- New option: `git idm track <identity> --directory <dir>`.  This will
  automatically track directories for this identity.  If you clone a
  project within the given path and make Git commits, then the identity will
  automatically be used as the author.
- New list behavior: `git idm list <identity> --tracked` will show the
  directories which have been tracked for a given identity.
- New remove behavior: If an identity is tracking directories, then removing the
  identity will automatically clean up the settings for tracking directories and
  authorship.
- New uninstall behavior: `git idm uninstall` will remove identity tracking
  along with the rest of `git idm` settings.

See also [GitHub issue 1][#1] for more information.

[#1]: https://github.com/samrocketman/git-identity-manager/issues/1

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
