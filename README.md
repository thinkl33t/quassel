Quassel IRC
===============

[![Quassel CI Build Status][ci-badge]][ci-status-page]

[Quassel IRC][web-home] is a modern, cross-platform, distributed IRC client,
meaning that one (or multiple) client(s) can attach to and detach from a
central core -- much like the popular combination of screen and a text-based
IRC client such as WeeChat, but graphical.

Not only do we aim to bring a pleasurable, comfortable chatting experience to
all major platforms, but it's free - as in beer and as in speech, since we
distribute Quassel under [the GPL](https://www.gnu.org/licenses/gpl.html), and
you are welcome to download and see for yourself!

## Release notes
You can find the current release notes on the [Quassel IRC homepage][web-home],
as well as in this repository's [`ChangeLog`][repo-changelog].

## Downloading
Official, stable downloads are provided on the [Quassel IRC download page](https://quassel-irc.org/downloads).

Untested, automated builds are available [for Windows](https://nightly.link/quassel/quassel/workflows/main/master/Windows.zip ) and [for macOS](https://nightly.link/quassel/quassel/workflows/main/master/macOS.zip ).  More details at [the nightly.link page](https://nightly.link/quassel/quassel/workflows/main/master ), by `oprypin`.  Or, if you are logged in to GitHub, pick any build from the [GitHub Actions tab][ci-status-page].

Unofficial builds and testing versions are [contributed by several community members](https://bugs.quassel-irc.org/projects/quassel-irc/wiki#Unofficial-builds).

## Quick reference
We recommend reading the [getting started guide on the wiki](https://bugs.quassel-irc.org/projects/quassel-irc/wiki#Getting-started),
but in a pinch, these steps will do.

On first run of the Quassel core, it will wait for a client to connect
and present a wizard that will allow you to create the database and one admin
user for the core-side storage.

Once you've set up Quassel, you may:
* Add more users: `quasselcore --add-user`
* Change the password of an existing user: `quasselcore --change-userpass=username`
* Delete a user (disconnecting any active session): `quasselcore --delete-user=username`
* List all users: `quasselcore --list-users`
* See all available options: `quasselcore --help`

For scripting, add `--json` to get a single machine-readable JSON document on
stdout (interactive prompts are suppressed; passwords are read from the
`QUASSEL_USER_PASSWORD` / `QUASSEL_NEW_PASSWORD` environment variables or,
when those are not set, silently from stdin):

```bash
$ quasselcore --list-users --json
{"ok":true,"command":"list-users","result":{"users":{"1":"admin","2":"alice"}}}

$ quasselcore --add-user --username=bob --json
{"ok":true,"command":"add-user","result":{"username":"bob"}}

# ...or pipe the username and password via stdin instead:
$ printf 'bob\nsecret\n' | quasselcore --add-user --json
{"ok":true,"command":"add-user","result":{"username":"bob"}}

$ quasselcore --delete-user=bob --json
{"ok":true,"command":"delete-user","result":{"username":"bob","hadActiveSession":true}}
```

On some systems, you may need to specify `--configdir`, e.g.
`quasselcore --configdir=/var/lib/quassel [command]`.

To learn more, see [the Quassel project wiki](https://bugs.quassel-irc.org/projects/quassel-irc/wiki) for in-depth
documentation.

## Getting involved

IRC is the preferred means of getting in touch with the developers.

The Quassel IRC Team can be contacted on **`Libera Chat/#quassel`**
(or **`#quassel.de`**).  If you have trouble getting Quassel to connect,
you can use [Libera Chat's web client](https://web.libera.chat/?channels=#quassel).

We always welcome new users in our channels!

You can learn more and reach out to us in several ways:
* [Visit our homepage][web-home]
* [Submit and browse issues on the bugtracker](https://bugs.quassel-irc.org)
  * GitHub issues are not used, but [pull requests](https://github.com/quassel/quassel/pull/new/master) are accepted!
* [Email the dev team - devel@quassel-irc.org][dev-email]

Thanks for reading,

~ *The Quassel IRC Team*

[web-home]: https://quassel-irc.org
[dev-email]: mailto:devel@quassel-irc.org
[repo-changelog]: ChangeLog
[ci-badge]: https://github.com/quassel/quassel/workflows/Quassel%20CI/badge.svg?branch=master
[ci-status-page]: https://github.com/quassel/quassel/actions?query=branch%3Amaster
