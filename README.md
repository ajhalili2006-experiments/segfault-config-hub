# ~ajhalili2006's config for segfault.net based disposable root servers

These disposable root servers are Docker containers inside [segfault.net](https://thc.org/segfault),
mostly for experimenting with hacking tools as part of improving my security posture and having
a field day in all things Linux.

## Directory structure

```tree
.
├── home
├── repos
├── root - Root user home directory
├── usr - userspace
└── www - By default, segfault provides one with pelican, but I use Mkdocs so this will be a submodule.
```

## Using the repo

```bash
# init a fresh container with a new SECRET
ssh root@segfault.net
# or use an existing one: ssh -o "SetEnv SECRET=whateveryouwanttoleakhere root@segfault.net"
# (in MobaXterm, ssh to secret@segfault.net first and paste your secret to prompt)

# go to /sec, init git repo and add the remotes
cd /sec && git init
git remote add hut ssh://git@git.sr.ht/~ajhalili2006-experiments/segfault-config-hub
git remote add lab ssh://git@mau.dev/ajhalili2006-experiments/segfault-config-hub

# remind me to have the SSH and GPG keys needed and their respective agents are fired up
# either manually or via keychain

# fetch 'em all!
git fetch --all

# bless anyone on this
git checkout -f main

# to make changes effect immediately, just trigger the big guns and ssh again
halt # or kill 1
```

### Doing this locally

The sources are at <https://github.com/hackerschoice/segfault/tree/main/guest>,
but be warned that the image size will go horribly to 50+ GBs on first build.
