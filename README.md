# tmux sessionizer

![tmux sessionizer example](./docs/images/example.jpg)

## Requirements

- [fzf](https://github.com/junegunn/fzf)
- [tmux](https://github.com/tmux/tmux)

## Configuration

Example of configuration file (stored at `$HOME/.config/tmux-sessionizer/sessions`)

```
~/src/*:src/%
~/tmp/*:tmp/%
~/.dotfiles:dotfiles
```

Format of each line is `pattern:name`, where `pattern` is a **glob pattern** to match directories, that correspond with sessions named `name`.

- For each `pattern`, `~` is expanded to `$HOME`
- For each `name`, `%` is expanded to basename of directory, specified by `pattern`

## Usage

To use tmux-sessionizer, simply run the executable file without arguments: `./tmux-sessionizer`.
It opens a fuzzy-finder with already opened tmux sessions as well as ones specified in `$HOME/.config/tmux-sessionizer/sessions`.
If a session has been chosen, `./tmux-sessionizer` will open this session or create one if it does not exist (in directory, specified in configuration file).

### Integration with tmux

Nice way to use tmux-sessionizer is through binding key to open tmux popup, for example:

```
# at $HOME/.config/tmux/tmux.conf
bind-key j display-popup -x 10% -y 10% -w 60% -h 60% -E "<path to tmux-sessionizer>"
```
