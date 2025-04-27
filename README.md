# kickstart.nvim

following the recommended setup as described here:
https://github.com/nvim-lua/kickstart.nvim?tab=readme-ov-file#recommended-step

if you directly modify the init.lua from the repo that you cloned from nvim-lua,
you will need to branch off your local changes when you want to pull the latest
changes from the upstream.

a better way is to fork your own copy, and make changes only in the forked repo,
and handle the conflict whenever you need to pull the latest from upstream.
```bash
$ git remote -v
origin	git@github.com:WhyAitchYou/kickstart.nvim.git (fetch)
origin	git@github.com:WhyAitchYou/kickstart.nvim.git (push)
upstream	https://github.com/nvim-lua/kickstart.nvim.git (fetch)
upstream	https://github.com/nvim-lua/kickstart.nvim.git (push)

$ git fetch upstream
$ git merge upstream/master
```

to make neovim load this repo, you need to create a symlink to the entire folder,
not just the init.lua file. this is because neovim will use the location of init.lua
to search for other companion files, such as lazy-lock.json, .stylua.toml.

```bash
$ git clone https://github.com/WhyAitchYou/kickstart.nvim.git ~/workdir/
$ ln -s ~/workdir/kickstart.nvim/ ~/.config/nvim
```

## changes differ from upstream

- version-control lazy-lock.json

the upstream repo doesn't check in `lazy-lock.json` but it's good for pinning the version. i remove `lazy-lock.json` from .gitignore.
