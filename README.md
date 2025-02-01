# Custom Configs

## `dracula.custom.omp.json`
A customized version of the [Dracula Oh My Posh config](https://github.com/JanDeDobbeleer/oh-my-posh/blob/main/themes/dracula.omp.json).

```bash
cat ~/.zshrc
# ...
eval "$(oh-my-posh init zsh --config https://raw.githubusercontent.com/jrdnbradford/terminal-configs/refs/heads/main/dracula.custom.omp.json)"

if [ "$TERM_PROGRAM" != "Apple_Terminal" ]; then
  eval "$(oh-my-posh init zsh)"
fi
# ...
```
