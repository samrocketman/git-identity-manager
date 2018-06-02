# Git Identity Manager

Ever find that managing multiple git identities is a pain?  This git transport
attempts to make it less painful.

![Knowing who you are can be painful][backpain]

[Image credit PBS.org][pbs]

# Installation

Add `git-idm` script to your `$PATH` and make it executable.  Then, you can
access the script via `git idm`.  See `git idm help` for usage.

# Uninstall

    git idm uninstall

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

# License

[MIT License](LICENSE.txt)

[backpain]: https://user-images.githubusercontent.com/875669/40868569-f1512a4e-65c2-11e8-9dfe-91ece96d62db.jpg
[pbs]: https://www.pbs.org/newshour/health/back-pain-industry-taking-patients-unhealthy-ride
