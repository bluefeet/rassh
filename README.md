# rassh - Re-Animated SSH

At @work we have some remote developers that were tired of dealing with lost
SSH connections.  We looked into [mosh](https://mosh.mit.edu/) but had some
security concerns, so in the interim I thought some vanilla SSH+screen might
do the job.  This is the result.

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

# Changes

## 2015-04-30

- Added documentation via `--help`, `-h`, or `help`.
- Exit earlier if the initial connection fails.
- Added the `--screen-cmd` and `--no-screen-cmd` options for those that
  don't like the default `bash --login`.
- Began spreading rassh!

# Contributing

To contribute to rassh you can open [an issue](https://github.com/bluefeet/rassh/issues)
or [make a fork](https://github.com/bluefeet/rassh#fork-destination-box)
and submit a pull request.

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
