# tmux-opencode-session-manager

Run many [opencode](https://opencode.ai) sessions across your projects — each in
its own tmux popup — then **list them, see which are busy vs. done, and jump to
one** from a single picker.

Adapted from [craftzdog/tmux-claude-session-manager](https://github.com/craftzdog/tmux-claude-session-manager)
for opencode. Sessions live on a dedicated tmux server socket so press `prefix + u` — a
pickup is just a few seconds away.

![tmux-opencode-session-manager](screenshot.png)

## Install

Clone this repo to your tmux plugins directory and enable it in your tmux config:

```sh
mkdir -p ~/.config/tmux/plugins && cd ~/.config/tmux/plugins
git clone https://github.com/<you>/tmux-opencode-session-manager
```

Then in `~/.tmux.conf` or `~/.config/tmux/tmux.conf`, add:

```
run-shell ~/.config/tmux/plugins/tmux-opencode-session-manager/opencode_session_manager.tmux
```

Reload with `tmux source-file ~/.config/tmux/tmux.conf`.

### Prerequisites

- tmux >= 3.2 (`display-popup`)
- [fzf](https://github.com/junegunn/fzf) for the picker
- opencode CLI

## Usage

| Key            | Action                                          |
| -------------- | ----------------------------------------------- |
| `prefix + y`   | Open opencode for the current directory         |
| `prefix + u`   | Open the session picker                         |

In the picker: `enter` jumps to a session, `ctrl-x` kills it. Sessions waiting
on you sort to the top in color.

### Options

```
set -g @opencode_launch_key  'y'              # launch key
set -g @opencode_list_key    'u'              # picker key
set -g @opencode_command     'opencode'       # command to run
set -g @opencode_socket      'opencode-popup' # dedicated tmux socket
set -g @opencode_popup_width '90%'            # popup width
set -g @opencode_popup_height '90%'           # popup height
```

## Status

Optional: install the opencode status plugin that stamps each session
`working` / `waiting` / `idle` on opencode events. Without it, the picker still
lists, previews, jumps, and kills — sessions just show `?` instead of a color.

## License

MIT