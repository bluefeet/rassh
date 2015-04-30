# rassh - Re-Animated SSH

At @work we have some remote developers that were tired of dealing with lost
SSH connections.  We looked into [mosh](https://mosh.mit.edu/) but had some
security concerns, so in the interim I thought some vanilla SSH+screen might
do the job.  This is the result.

rassh is pretty simple.  It executes ssh, telling it to run screen on the
remote host when connected.  A symlink is made from `~/.ssh/rassh_auth_socket`
to wherever the real auth socket is.  This symlink is maintaned between
disconnects so agent forwarding should keep working.

Simply:

```
ssh foo.example.com
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
