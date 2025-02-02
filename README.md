# Custom Configs

## `dracula.custom.omp.json`
A customized version of the [Dracula Oh My Posh config](https://github.com/JanDeDobbeleer/oh-my-posh/blob/main/themes/dracula.omp.json) set to autoupdate from GitHub.

```bash
cat ~/.zshrc
# ...
LOCAL_DRACULA_OMP="$HOME/dracula.custom.omp.json"
REMOTE_DRACULA_OMP="https://raw.githubusercontent.com/jrdnbradford/terminal-configs/refs/heads/main/dracula.custom.omp.json"

TEMP_FILE=$(mktemp)

if curl -s -o "$TEMP_FILE" "$REMOTE_DRACULA_OMP"; then
    if [ ! -f "$LOCAL_DRACULA_OMP" ]; then
        echo "Downloading Dracula OMP config"
        mv "$TEMP_FILE" "$LOCAL_DRACULA_OMP"
    else
        if ! cmp -s "$LOCAL_DRACULA_OMP" "$TEMP_FILE"; then
            echo "Updating Dracula OMP config"
            mv "$TEMP_FILE" "$LOCAL_DRACULA_OMP"
        else
            # echo "Files are identical, no update needed."
            rm "$TEMP_FILE"
        fi
    fi
else
    echo "Error: Failed to download the remote Dracula OMP config."
    rm -f "$TEMP_FILE"
fi

eval "$(oh-my-posh init zsh --config "$LOCAL_DRACULA_OMP")"
# ...
```
