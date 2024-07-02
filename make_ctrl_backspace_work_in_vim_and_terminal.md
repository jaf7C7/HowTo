# How To Make Ctrl-Backspace Work In Vim And Terminal

In the terminal:
```
# Find out what char Ctrl-Backspace emits (usually '^H')
$ stty werase ''    # Disable 'werase'
$ ^H^H^H            # Press Ctrl-Backspace a few times
$ stty werase '^H'  # So we change 'werase' to '^H'
```

In vim:
```
" In Vim Ctrl-Backspace should always be equivalent to Ctrl-H. So we remap
" Ctrl-H (i.e. Ctrl-Backspace) to Ctrl-W in insert and command mode.
:inoremap <C-H> <C-W>
:cnoremap <C-H> <C-W>
```
