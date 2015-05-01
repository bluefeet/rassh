# rassh - Re-Animated SSH

At @work we have some remote developers that were tired of dealing with lost
SSH connections.  We looked into [mosh](https://mosh.mit.edu/) but had some
security concerns (nothing in particular, mosh is awesome), so in the interim
I thought some vanilla SSH+screen might do the job.  This is the result.

rassh is pretty simple.  It executes ssh, telling it to run screen on the
remote host when connected.  A symlink is made from `~/.ssh/rassh_auth_socket`
to wherever the real auth socket is.  This symlink is maintained between
disconnects so agent forwarding should keep working.

Simply:

```
rassh foo.example.com
```

And you'll now have a login session on the remote host that will survive
jittery networks.  Yay!

# Documentation

Various command line options are available to customize rassh' behavior.  They can
be found with:

```
rassh help
```

# Installaion

Just copy the `rassh` standalone script to some location such as `~/bin` or
`/usr/bin`.  rassh requires perl and ssh.  The remote system must have
screen installed.

# Alternatives

- [mosh](https://mosh.mit.edu/)
- [autossh](http://www.harding.motd.ca/autossh/)
- [autossh + tmux = smux](https://coderwall.com/p/aohfrg/smux-ssh-with-auto-reconnect-tmux-a-mosh-replacement)

# Changes

## 2015-05-01

- Added the `--sleep=` and `--retries=` options.

## 2015-04-30

- More reasonable flapping timing.
- Added documentation via `--help`, `-h`, or `help`.
- Exit earlier if the initial connection fails.
- Added the `--screen-cmd` and `--no-screen-cmd` options for those that
  don't like the default `bash --login`.
- Began spreading rassh!

# Contributing

To contribute to rassh you can open [an issue](https://github.com/bluefeet/rassh/issues)
or [make a fork](https://github.com/bluefeet/rassh) and submit a pull request.

# License

The MIT License (MIT)

Copyright (c) 2015 Aran Deltac

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
