# Control characters conflict with Emacs

- In `st`, `\033` is `ESC`
- Complicated characters are sent as a sequence with either `ESC O` (`\033O`) as
  a prefix or `ESC [` (`\033[`) as a prefix.
- Emacs understands most of this and has mapping for these prefixes.
- Rebinding any of these prefixes in the ignores supresses the emacs predefined
  bindings and causes very weird (yet understandable) behaviour.
- We can capture `ESC O` in the terminal itself on the top level and send it as
  a custom control sequence and use that control sequence for custom mapping in
  emacs.

## Current use-case

- Capture `ESC O` in the top level and send it as `\033[23;5~` (`F35`).
- Use `F35` for binding in emacs.

# References

- https://emacs.stackexchange.com/questions/68703/m-causes-emacs-to-print-weird-possibly-escape-sequences
;; https://emacs.stackexchange.com/questions/1020/problems-with-keybindings-when-using-terminal/13957#13957
- https://invisible-island.net/xterm/ctlseqs/ctlseqs.html#h2-Special-Keyboard-Keys
