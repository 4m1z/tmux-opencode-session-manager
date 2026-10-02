# tmux-opencode-session-manager

Manage OpenCode sessions in tmux popups. Launch sessions by project, view their status in a picker, and return to any session.

## Requirements

- tmux 3.2 or later
- [fzf](https://github.com/junegunn/fzf)
- OpenCode v2
- Bash and Python 3

## Install

Add this to `~/.tmux.conf` or `~/.config/tmux/tmux.conf`:

```sh
run-shell ~/.config/tmux/plugins/tmux-opencode-session-manager/opencode_session_manager.tmux
```

Reload tmux with `prefix` + `r`.

## Use

- `prefix` + `y`: launch or resume a session for the current directory
- `prefix` + `u`: open the session picker
- `enter`: jump to the selected session
- `tab`: expand or collapse session details
- `ctrl-x`: kill the selected session

## Status plugin

Install the plugin for live status updates:

```sh
opencode plugin add opencode-tmux-session-status@latest
```

Restart the OpenCode service after installation. The picker can also resolve status from the OpenCode API without the plugin.

## Configuration

Options can be set on the main tmux server before loading the plugin:

| Option | Default | Description |
| --- | --- | --- |
| `@opencode_launch_key` | `y` | Launch key |
| `@opencode_list_key` | `u` | Picker key |
| `@opencode_command` | `opencode` | Command to run |
| `@opencode_session_prefix` | `oc_` | Session name prefix |
| `@opencode_socket` | `opencode-popup` | Dedicated tmux socket |
| `@opencode_popup_width` | `90%` | Popup width |
| `@opencode_popup_height` | `90%` | Popup height |

## Tests

```sh
bash scripts/tests.sh
```

## License

MIT
