# my-lfrc

## fix work directory

refer: https://github.com/gokcehan/lf/blob/master/etc/lfcd.sh

> zshrc
> add code into .zshrc

```bash
lfcd () {
    tmp="$(mktemp)"
    # `command` is needed in case `lfcd` is aliased to `lf`
    command lf -last-dir-path="$tmp" "$@"
    if [ -f "$tmp" ]; then
        dir="$(cat "$tmp")"
        rm -f "$tmp"
        if [ -d "$dir" ]; then
            if [ "$dir" != "$(pwd)" ]; then
                cd "$dir"
            fi
        fi
    fi
}
```

## keybind

> zshrc

```bash
bindkey -s '^o' 'lfcd\n'
```
