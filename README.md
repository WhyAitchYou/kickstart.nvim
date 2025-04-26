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
```

## changes differ from upstream

- version-control lazy-lock.json

the upstream repo doesn't check in `lazy-lock.json` but it's good for pinning the version.
because i symlink the `~/.config/nvim/init.lua` to the `init.lua` in this fork repo,
i have to tell nvim where to generate the `lockfile`
```lua
require("lazy").setup({
  -- Your plugins here
}, {
  lockfile = vim.fn.expand("~/workdir/kickstart.nvim/lazy-lock.json"),
})
```
