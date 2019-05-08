# VSCode

[Shortcuts reference](https://code.visualstudio.com/shortcuts/keyboard-shortcuts-macos.pdf)

| Shortcut          | Description            | VSCode Name            | Custom shortcut?       |
|-------------------|------------------------|------------------------|------------------------|
| `⌘ + P`           |  Go to file dialog     |||
| `⌘ + ⇧ + P`       |  Shortcut dialog       |||
| `⌘ + ⇧ + /`       |  Focus editor          | View: Focus Next Editor Group |  ✓ |
| `⌘ + ⇧ + T`       |  Focus terminal        | Terminal: Focus Terminal |  ✓ |
| `⌘ + ⇧ + E`       |  Focus file explorer   | View: Show Explorer ||
| `⌘ + K , ↵`       |  Keep editor page open | View: Keep Editor ||
| `⌘ + K , ⌘ + W`   |  Close all open tabs   | View: Close All Editors ||
| `⌘ + ⇧ + [`       |  Next tab              | View: Open Next Editor ||
| `⌘ + ⇧ + ]`       |  Prev tab              | View: Open Previous Editor ||
| `⌘ + ↓`           |  Open editor from explorer | |  ✓ |
| `⌥ + ⌘ + C`       | Collapse explorer folders | File: Collapse Folders in Explorer |  ✓ |
| `^ + -`           | Go back from definition | | |
| `^ + =`           | Go to definition | | ✓ |
| `^ + ⌥ + Z`       | Refresh git            | Refresh git | ✓ |

Chrome

| Shortcut          | Description            |
| `⌥ + ⌘ + →`       | Next tab               |

⌘ = Command
^ = Control
↵ = Enter
→ = Tab
⌥ = Option (/Alt)

## Choose tab

```text
Control + [Tab number]
```

## Go to definition

Usually you can Cmd + Click or use `F12`

## Go back from defintion

Preferences > Keyboard Shortcut > workbench.action.navigateBack:

```text
Cntrl + -
```

## List all functions in a script

Preferences > Keyboard Shortcut > workbench.action.gotoSymbol:

```text
Cmd + Shift + O
(optionally then type ':')
```

## Add `code` to terminal

See [this page](https://code.visualstudio.com/docs/setup/mac) for adding VSCode to the path so that you can run e.g.

```bash
code some_directory
```