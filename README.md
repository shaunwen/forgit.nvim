# forgit.nvim

forgit plugin for neovim. Run git interactively with fzf inside nvim.

This plug is a wrapper for [forgit](https://github.com/wfxr/forgit) by `Wenxuan Zhang`

You need

- [install forgit](https://github.com/wfxr/forgit)
- [fzf](https://github.com/junegunn/fzf) so you can confirm/select the matches to apply your changes
- by default the plugin using [fd](https://github.com/sharkdp/fd) to list all files in the current folder, you can use
  `git ls_file`
- a pager tool, e.g. `delta`

https://user-images.githubusercontent.com/1681295/207864539-ec65b9c4-d8a0-4509-b13f-bd2192f742d9.mp4

# install

```
Plug 'ray-x/guihua.lua'  "lua GUI lib
Plug 'ray-x/forgit.nvim'
```

# Configure

```lua
require'forgit'.setup({
  diff = 'delta', -- you can use `diff`, `diff-so-fancy`
  ls_file = 'fd', -- also git ls_file
  exact = false, -- exact match
  vsplit = true, -- split forgit window the screen vertically, when set to number
  -- it is a threadhold when window is larger than the threshold forgit will split vertically,
  height_ratio = 0.6, -- height ratio of forgit window when split horizontally
  width_ratio = 0.6, -- height ratio of forgit window when split vertically
  git_alias = true,  -- git commands alias (see readme)
  fugitive = false, -- -- git fugitive installed
})
```

# Screenshot

![ga](https://user-images.githubusercontent.com/1681295/207861513-4a22c804-0e4c-46f5-92a1-f1d0c8d5e02a.jpg)

![gbd](https://user-images.githubusercontent.com/1681295/207861692-8c756b00-6e29-4e41-8fd4-dbf8b604fb7a.jpg)


# usage

- If you put your cursor on the word want to replace or visual select the word you want to replace, simply run

| Command               | Action                    |
| :-------------------: | ------------------------- |
|Ga      | Interactive `git add` generator |
|Glo     | Interactive `git log` generator |
|Gi      | Interactive .gitignore generator |
|Gd      | Interactive `git diff` viewer |
|Grh     | Interactive `git reset HEAD <file>` selector |
|Gcf     | Interactive `git checkout <file>` selector |
|Gcb     | Interactive `git checkout <branch>` selector |
|Gbd     | Interactive `git branch -D <branch>` selector |
|Gct     | Interactive `git checkout <tag>` selector |
|Gco     | Interactive `git checkout <commit>` selector |
|Grc     | Interactive `git revert <commit>` selector |
|Gss     | Interactive `git stash` viewer |
|Gsp     | Interactive `git stash push` selector |
|Gclean  | Interactive `git clean` selector |
|Gcp     | Interactive `git cherry-pick` selector |
|Grb     | Interactive `git rebase -i` selector |
|Gbl     | Interactive `git blame` selector |
|Gfu     | Interactive `git commit --fixup && git rebase -i --autosquash` selector |

- Other git + fzf commands

| Command               | Action                    |
| :-------------------: | ------------------------- |
|Gdl      | Interactive `git diff --name-only & edit select file` generator |
|Gcbc     | Interactive `git branch --sort=-committerdate && checkout` generator |
|Gdc     | Interactive `git diff hash` generator |

### ⌨  Forgit Keybinds

| Key                                           | Action                    |
| :-------------------------------------------: | ------------------------- |
| <kbd>Enter</kbd>                              | Confirm                   |
| <kbd>Tab</kbd>                                | Toggle mark and move up   |
| <kbd>Shift</kbd> - <kbd>Tab</kbd>             | Toggle mark and move down |
| <kbd>?</kbd>                                  | Toggle preview window     |
| <kbd>Alt</kbd> - <kbd>W</kbd>                 | Toggle preview wrap       |
| <kbd>Ctrl</kbd> - <kbd>S</kbd>                | Toggle sort               |
| <kbd>Ctrl</kbd> - <kbd>R</kbd>                | Toggle selection          |
| <kbd>Ctrl</kbd> - <kbd>Y</kbd>                | Copy commit hash*         |
| <kbd>Ctrl</kbd> - <kbd>K</kbd> / <kbd>P</kbd> | Selection move up         |
| <kbd>Ctrl</kbd> - <kbd>J</kbd> / <kbd>N</kbd> | Selection move down       |
| <kbd>Alt</kbd> - <kbd>K</kbd> / <kbd>P</kbd>  | Preview move up           |
| <kbd>Alt</kbd> - <kbd>J</kbd> / <kbd>N</kbd>  | Preview move down         |


### ⌨  Git command alias


| Command               | Action                    |
| :-------------------: | ------------------------- |
|Gaa| git add --all|
|Gap| git  add -pu |
|Gash| git  stash |
|Gasha| git  stash apply |
|Gashp| git  stash pop |
|Gashu| git  stash --include-untracked |
|Gau| git  add -u |
|Gc| git  commit |
|Gce| git  clean |
|Gcef| git  clean -fd |
|Gcl| git  clone |
|Gcm| git  commit -m |
|GcB| git checkout -b <branch> |
|Gdf| git  diff -- |
|Gdnw| git  diff -w -- |
|Gdw| git  diff --word-diff |
|Gdmn| git  diff master/main --name-only \| fzf |
|Gdn| git  diff --name-only \| fzf |
|Gf| git  fetch |
|Gfa| git  fetch --all |
|Gfr| git  fetch; and git rebase |
|Glg| git  log --graph --max-count=5 |
|Gm| git  merge |
|Gmff| git  merge --ff |
|Gmnff| git  merge --no-ff |
|Gopen| git  config --get remote.origin.url | xargs open |
|Gpl| git  pull |
|Gplr| git  pull --rebase |
|Gps| git  push |
|Gpsf| git  push --force-with-lease |
|Gr| git  remote -v |
|Grb| git  rebase |
|Grbi| git  rebase -i |
|Grs| git  reset -- |
|Grsh| git  reset --hard |
|Grsl| git  reset HEAD~ |
|Gs| git  status |
|Gsh| git  show |
|Gt| git  tag |
|Gtop| git  rev-parse --show-toplevel |
|Gurl| git  config --get remote.origin.url |

### 📦 Optional dependencies

- [`delta`](https://github.com/dandavison/delta) / [`diff-so-fancy`](https://github.com/so-fancy/diff-so-fancy): For better human readable diffs.

- [`bat`](https://github.com/sharkdp/bat.git): Syntax highlighting for `gitignore`.

- [`emoji-cli`](https://github.com/wfxr/emoji-cli): Emoji support for `git log`.

- git fugitive
