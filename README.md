# Git Identity Manager

Ever find that managing multiple git identities is a pain?  This git transport
attempts to make it less painful.

![Knowing who you are can be painful][backpain]

[Image credit PBS.org][pbs]

# Requirements

- Git 2.18 or later.
  - [`git 2.10` or later because of `core.sshCommand`][git-2.10].
  - [`git 2.13` or later because of `includeIf.<condition>.path`][git-2.13].
  - [`git 2.18` or later because of git-config bug][git-2.18].
- GNU bash
- awk (BSD or GNU awk recommended)
- sed (BSD or GNU sed recommended)
- openssh client with ssh-agent

bash, awk, sed, and openssh are available by default on Mac OS X, BSD, and most
flavors of GNU/Linux.  Git likely needs to be installed.  On Mac OS X,
installing Git through homebrew is recommended.

# Installation

Add `git-idm` script to your `$PATH` and make it executable.  Then, you can
access the script via `git idm`.  See `git idm help` for usage.

### via Homebrew on macOS / Linux / WSL2

A Homebrew tap is available [here](https://github.com/fleetwoodmac/homebrew-git-identity-manager).

Install with the following command.

    brew install fleetwoodmac/git-identity-manager/git-identity-manager`

# Uninstall

Remove all data stored in `$HOME/.gitconfig` related to `git idm`.  This will
not affect settings used by git.

    git idm uninstall

### via Homebrew 
- If installed via Homebrew, uninstall by first running `git idm uninstall` as above.
- Then, run `brew uninstall git-identity-manager`
- Finally, run `brew untap fleetwoodmac/git-identity-manager`


# Quick start

Add your first identity.

    git idm add jcool --name "Joe Cool" --email joe@example.com --key ~/.ssh/id_rsa

Activate your identity.

    git idm use jcool

Show which identity is active.

    git idm active

List all known identities.

    git idm list

For more commands see `git idm help`.

# Autotracked identities

You can configure your Git identities to automatically switch depending on what
directory you have cloned.  For example, let's say you have personal projects
and work projects on the same laptop.  Assuming you have a `work` identity and a
`personal` identity configured, the following commands would help you
auto-switch identites for repositories under designated paths.

    git idm track work --directory ~/git/work
    git idm track personal --directory ~/git/github

You can list what directories are tracked by a given identity.

    git idm list work --tracked

Which will return output like the following.

```
work identity will automatically apply to the following directories:
    /home/user/git/work/
```

Verify the identity has switched with `git config user.email`.

    cd ~/git/work
    mkdir example
    cd example/
    git init

    # the email identity should show your work email
    git config user.email

# License

[MIT License](LICENSE.txt)

[backpain]: https://user-images.githubusercontent.com/875669/40868569-f1512a4e-65c2-11e8-9dfe-91ece96d62db.jpg
[build-img]: https://travis-ci.org/samrocketman/git-identity-manager.svg?branch=main
[build-status]: https://travis-ci.org/samrocketman/git-identity-manager
[git-2.10]: https://github.com/git/git/blob/v2.10.0/Documentation/RelNotes/2.10.0.txt#L83-L84
[git-2.13]: https://github.com/git/git/blob/v2.13.0/Documentation/RelNotes/2.13.0.txt#L127-L130
[git-2.18]: https://github.com/git/git/blob/53f9a3e157dbbc901a02ac2c73346d375e24978c/Documentation/RelNotes/2.18.0.txt#L379-L384
[pbs]: https://www.pbs.org/newshour/health/back-pain-industry-taking-patients-unhealthy-ride
