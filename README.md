# tmux-vim-select-pane

## Deprecated

This script should no longer be necessary. It's possible to inline the
script directly into the tmux configuration using tmux `if-shell` commands. For
more on this approach see the [thoughtbot blog post][thoughtbot] or the readme
for [vim-tmux-navigator][navigator]. Issue with inline scripting can be opened
in the vim-tmux-navigator repository.

## Overview

This is a repackaging of the split pane switching script used in
[Mislav Marohnić's][mislav] tmux-navigator configuration described in this
[gist][gist].

## Installation

Please note that this is only the script used to switch panes. To fully enable
this functionality you will need to follow the instructions below (assumes
[homebrew][brew] and [vundle][vundle]).

1. Install tmux-vim-select-pane:
```bash
brew install
https://raw.github.com/derekprior/tmux-vim-select-pane/master/tmux-vim-select-pane.rb
```

2. Add the [vim-tmux-navigator][navigator] plugin to vim:
```vim
Bundle 'christoomey/vim-tmux-navigator'
```

3. Add the following configuration to your `~/.tmux-conf` configuration
```tmux
# Smart pane switching with awareness of vim splits
bind -n C-k run-shell 'tmux-vim-select-pane -U'
bind -n C-j run-shell 'tmux-vim-select-pane -D'
bind -n C-h run-shell 'tmux-vim-select-pane -L'
bind -n C-l run-shell 'tmux-vim-select-pane -R'
bind -n "C-\\" run-shell 'tmux-vim-select-pane -l'
```

## Manual Installation

If you are not a homebrew user, you can download `bin/tmux-vim-select-pane` from
this repository, add it to a directory in your path and mark it as executable.

vim-tmux-navigator has pathogen installation instructions in its readme.

[thoughtbot]:http://robots.thoughtbot.com/post/53022241323/seamlessly-navigate-vim-and-tmux-splits
[mislav]:http://mislav.uniqpath.com/
[gist]:https://gist.github.com/mislav/5189704
[brew]:https://github.com/mxcl/homebrew/
[vundle]:https://github.com/gmarik/vundle
[navigator]:https://github.com/christoomey/vim-tmux-navigator
