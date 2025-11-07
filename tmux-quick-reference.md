# 📋 Tmux Quick Reference Card

> **Prefix Key:** `Ctrl+b` (Press together, release, then press command key)

---

## 🎯 Sessions

| Command | Action |
|---------|--------|
| `tmux` | Start new session |
| `tmux new -s name` | Start named session |
| `tmux ls` | List all sessions |
| `tmux attach -t name` | Attach to session |
| `tmux kill-session -t name` | Kill session |
| **Inside Tmux:** | |
| `Ctrl+b d` | Detach from session |
| `Ctrl+b s` | Show session list |
| `Ctrl+b $` | Rename session |
| `Ctrl+b (` | Previous session |
| `Ctrl+b )` | Next session |

---

## 🪟 Windows (Tabs)

| Command | Action |
|---------|--------|
| `Ctrl+b c` | Create new window |
| `Ctrl+b ,` | Rename window |
| `Ctrl+b n` | Next window |
| `Ctrl+b p` | Previous window |
| `Ctrl+b 0-9` | Switch to window # |
| `Ctrl+b w` | List windows |
| `Ctrl+b &` | Kill window |
| `Ctrl+b l` | Last active window |

---

## 📐 Panes (Splits)

### Creating Panes

| Command | Action |
|---------|--------|
| `Ctrl+b \|` | Split vertical (left/right) |
| `Ctrl+b -` | Split horizontal (top/bottom) |

### Navigating Panes (Vim-style)

| Command | Action |
|---------|--------|
| `Ctrl+b h` | Move to left pane |
| `Ctrl+b j` | Move to bottom pane |
| `Ctrl+b k` | Move to top pane |
| `Ctrl+b l` | Move to right pane |
| `Ctrl+b ←↑→↓` | Move with arrow keys |
| `Ctrl+b o` | Cycle through panes |
| `Ctrl+b q` | Show pane numbers |

### Resizing Panes

| Command | Action |
|---------|--------|
| `Ctrl+b H` | Resize left |
| `Ctrl+b J` | Resize down |
| `Ctrl+b K` | Resize up |
| `Ctrl+b L` | Resize right |

### Managing Panes

| Command | Action |
|---------|--------|
| `Ctrl+b x` | Kill pane |
| `Ctrl+b z` | Zoom pane (fullscreen toggle) |
| `Ctrl+b !` | Break pane to new window |
| `Ctrl+b Space` | Cycle layouts |

---

## 📝 Copy Mode (Scroll & Copy)

| Command | Action |
|---------|--------|
| `Ctrl+b [` | Enter copy mode |
| **In Copy Mode:** | |
| `h j k l` | Move cursor (vim style) |
| `Arrow keys` | Move cursor |
| `Space` | Start selection |
| `Enter` | Copy and exit |
| `q` | Quit copy mode |
| `/` | Search forward |
| `?` | Search backward |
| `n` | Next search result |
| `g` | Go to top |
| `G` | Go to bottom |
| **Outside Copy Mode:** | |
| `Ctrl+b ]` | Paste copied text |

---

## 🖱️ Mouse Support

✅ Click panes to switch  
✅ Click windows in status bar  
✅ Drag borders to resize  
✅ Scroll with mouse wheel  
✅ Select text (auto-copies)  
✅ Right-click or `Ctrl+Shift+V` to paste

---

## ⚙️ Help & Info

| Command | Action |
|---------|--------|
| `Ctrl+b ?` | List all key bindings |
| `Ctrl+b t` | Show clock |
| `Ctrl+b i` | Show pane info |
| `Ctrl+b :` | Enter command mode |
| `Ctrl+b r` | Reload config *(custom)* |

---

## 💡 Command Mode (`Ctrl+b :`)

```bash
# Resize panes
resize-pane -D 5              # Down 5 lines
resize-pane -U 5              # Up 5 lines
resize-pane -L 5              # Left 5 columns
resize-pane -R 5              # Right 5 columns

# Synchronized typing
setw synchronize-panes on     # Type in all panes at once
setw synchronize-panes off    # Turn off sync

# Window management
swap-window -s 2 -t 1         # Swap windows 2 and 1

# Layouts
select-layout even-vertical   # Stack panes vertically
select-layout even-horizontal # Stack panes horizontally
select-layout tiled           # Tile all panes
```

---

## 🔥 Common Patterns

### Development Setup
```bash
Ctrl+b c           # New window for server
Ctrl+b ,           # Rename to "server"
npm start
Ctrl+b 1           # Back to main window
Ctrl+b -           # Split horizontal
# Top: editor, Bottom: terminal
```

### Multiple Servers
```bash
Ctrl+b |           # Split vertical
ssh server1        # Left pane
Ctrl+b l           # Move right
ssh server2        # Right pane
Ctrl+b :           # Command mode
setw synchronize-panes on  # Type on both!
```

### Reading Logs
```bash
Ctrl+b [           # Enter copy mode
/error             # Search for "error"
n                  # Next match
q                  # Exit when done
```

---

## 🎨 Your Custom Config

✅ Session auto-starts as "main"  
✅ Time shows in 12-hour IST format  
✅ Modern blue/cyan color scheme  
✅ Vi-style pane navigation (h/j/k/l)  
✅ Intuitive split commands (| and -)  
✅ Mouse support enabled  
✅ Windows start at 1 (not 0)  
✅ 5000 lines scrollback

**Config file:** `~/.tmux.conf`  
**Reload:** `Ctrl+b r`

---

## 🆘 Survival Guide

| Problem | Solution |
|---------|----------|
| Lost? | `Ctrl+b ?` - Show all commands<br>`Ctrl+b w` - Show where you are |
| Pane too small? | `Ctrl+b z` - Zoom to fullscreen |
| Can't scroll? | `Ctrl+b [` - Enter copy mode |
| Want to exit? | `Ctrl+b d` - Detach (keeps running)<br>`exit` - Close current pane/window<br>`Ctrl+d` - Also closes |
| Forgot session? | `tmux ls` - List all sessions<br>Look at status bar (left shows name) |

---

## 📊 Cheat Sheet Summary

```
SESSION BASICS:
  tmux new -s name      → Start named session
  tmux attach -t name   → Attach to session
  Ctrl+b d              → Detach

WINDOWS (Tabs):
  Ctrl+b c              → Create window
  Ctrl+b n/p            → Next/Previous
  Ctrl+b 1-9            → Switch to window

PANES (Splits):
  Ctrl+b |/-            → Split vertical/horizontal
  Ctrl+b h/j/k/l        → Navigate (vim)
  Ctrl+b z              → Zoom pane
  Ctrl+b x              → Kill pane

COPY MODE:
  Ctrl+b [              → Enter
  Space                 → Start selection
  Enter                 → Copy
  Ctrl+b ]              → Paste

HELP:
  Ctrl+b ?              → All commands
  Ctrl+b :              → Command mode
```

---

**💾 Print this and keep it handy while learning tmux!**
