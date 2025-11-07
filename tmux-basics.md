# 📘 Tmux Basics - Complete Guide

## Table of Contents

- [What is Tmux?](#what-is-tmux)
- [Core Concepts](#core-concepts)
- [The Prefix Key](#the-prefix-key)
- [Starting Tmux](#starting-tmux)
- [Session Management](#session-management)
- [Window Management](#window-management)
- [Pane Management](#pane-management)
- [Copy Mode](#copy-mode)
- [Mouse Support](#mouse-support)
- [Common Workflows](#common-workflows)
- [Tips & Tricks](#tips--tricks)
- [Troubleshooting](#troubleshooting)

---

## What is Tmux?

**Tmux = Terminal Multiplexer**

Think of it as:
- 🪟 Multiple terminal windows in one
- 📁 A workspace manager for your terminal  
- 🔌 A way to keep programs running when you disconnect

### Key Benefits

✅ Run multiple terminals in one window  
✅ Split your screen into panes  
✅ Detach and reattach - your work persists  
✅ Perfect for SSH sessions (won't lose work if connection drops)  
✅ Organize different projects in different sessions

---

## Core Concepts

### Hierarchy

```
Session → Contains multiple Windows → Each window has multiple Panes
```

#### 1. **Session**
- Like a workspace or project
- You can have multiple sessions running
- Example: `work` session, `personal` session

#### 2. **Window**
- Like a tab in a browser
- Each session can have multiple windows
- Example: Window 1 = code, Window 2 = server, Window 3 = logs

#### 3. **Pane**
- Split sections within a window
- See multiple terminals at once
- Example: Code on left, terminal on right

### Visual Representation

```
┌─ Session: "work" ──────────────────────────────┐
│                                                 │
│  [Window 1: code] [Window 2: server] [Window 3]│
│  ┌────────┬─────┐                              │
│  │ Pane 1 │Pane2│  ← Window 1 split into panes │
│  │        │     │                               │
│  │  vim   │bash │                               │
│  └────────┴─────┘                               │
└─────────────────────────────────────────────────┘
```

---

## The Prefix Key

Almost all tmux commands start with: **`Ctrl+b`** (called the "prefix")

### How it works:
1. Press `Ctrl+b` (together)
2. Release both keys
3. Press the command key

### Example:
```
Ctrl+b then c  = Create new window
(Press Ctrl+b, release, then press c)
```

---

## Starting Tmux

### Basic Commands

```bash
# Start new session
tmux

# Start with a name
tmux new -s work

# Your .bashrc auto-starts with "main" session
# So just open a terminal!
```

---

## Session Management

### Listing Sessions

```bash
# List all sessions
tmux ls
tmux list-sessions  # same as above
```

### Creating Sessions

```bash
# New session named "myproject"
tmux new -s myproject

# New session "work", first window named "editor"
tmux new -s work -n editor
```

### Attaching to Sessions

```bash
# Attach to last session
tmux attach

# Attach to "work" session
tmux attach -t work
tmux a -t work        # short version
```

### Inside Tmux

| Command | Action |
|---------|--------|
| `Ctrl+b d` | Detach from current session |
| `Ctrl+b $` | Rename current session |
| `Ctrl+b s` | Show session list (interactive) |
| `Ctrl+b (` | Switch to previous session |
| `Ctrl+b )` | Switch to next session |

### From Command Line

```bash
# Kill specific session
tmux kill-session -t work

# Kill all except current
tmux kill-session -a

# Kill all sessions
tmux kill-server
```

---

## Window Management

Think of windows as **TABS** in a browser.

### Creating Windows

| Command | Action |
|---------|--------|
| `Ctrl+b c` | Create new window |

### Navigating Windows

| Command | Action |
|---------|--------|
| `Ctrl+b n` | Next window |
| `Ctrl+b p` | Previous window |
| `Ctrl+b 0-9` | Switch to window 0-9 |
| `Ctrl+b w` | List windows (interactive) |
| `Ctrl+b l` | Last active window |

### Managing Windows

| Command | Action |
|---------|--------|
| `Ctrl+b ,` | Rename window |
| `Ctrl+b &` | Kill window (asks for confirmation) |
| `Ctrl+b f` | Find window by name |

---

## Pane Management

Panes let you **SPLIT** your window into sections.

### Creating Panes (Your Custom Bindings)

| Command | Action |
|---------|--------|
| `Ctrl+b \|` | Split vertically (left/right) |
| `Ctrl+b -` | Split horizontally (top/bottom) |

### Navigating Panes (Your Custom Vim Bindings)

| Command | Action |
|---------|--------|
| `Ctrl+b h` | Move to left pane |
| `Ctrl+b j` | Move to bottom pane |
| `Ctrl+b k` | Move to top pane |
| `Ctrl+b l` | Move to right pane |

### Default Navigation (still works)

| Command | Action |
|---------|--------|
| `Ctrl+b ←↑→↓` | Move with arrow keys |
| `Ctrl+b o` | Cycle through panes |
| `Ctrl+b q` | Show pane numbers |

### Resizing Panes (Your Custom Bindings)

| Command | Action |
|---------|--------|
| `Ctrl+b H` | Resize left (capital H) |
| `Ctrl+b J` | Resize down |
| `Ctrl+b K` | Resize up |
| `Ctrl+b L` | Resize right |

### Managing Panes

| Command | Action |
|---------|--------|
| `Ctrl+b x` | Kill current pane |
| `Ctrl+b z` | Toggle zoom (fullscreen) |
| `Ctrl+b !` | Break pane into new window |
| `Ctrl+b {` | Move pane left |
| `Ctrl+b }` | Move pane right |
| `Ctrl+b Ctrl+o` | Rotate panes |
| `Ctrl+b Space` | Cycle through layouts |

---

## Copy Mode

By default, you can't scroll with mouse wheel in terminal. Copy mode lets you scroll and copy text.

### Enter Copy Mode

```
Ctrl+b [    # Enter copy mode
```

### In Copy Mode (Vi keys enabled)

| Key | Action |
|-----|--------|
| `h, j, k, l` | Move cursor (vim style) |
| `Arrow keys` | Also work |
| `Ctrl+u / Ctrl+d` | Page up/down |
| `g / G` | Top/bottom of buffer |
| `/ or ?` | Search forward/backward |
| `n / N` | Next/previous search result |
| `Space` | Start selection |
| `Enter` | Copy selection and exit |
| `q` | Quit copy mode |
| `Escape` | Also quits |

### Pasting

```
Ctrl+b ]    # Paste last copied text
```

---

## Mouse Support

Your config has mouse enabled! You can:

✅ Click on panes to switch  
✅ Click on windows in status bar  
✅ Drag borders to resize panes  
✅ Scroll with mouse wheel  
✅ Select text with mouse (copies automatically)

### To paste selected text:
- **Linux**: `Ctrl+Shift+V` or right-click
- **Mac**: `Cmd+V`

---

## Common Workflows

### Workflow 1: Development Setup

```bash
tmux new -s dev              # Start session
Ctrl+b c                     # New window for server
Ctrl+b -                     # Split for logs
Ctrl+b 1                     # Back to window 1
Ctrl+b |                     # Split for editor and terminal
```

**Result:**
```
Window 1: Editor | Terminal
Window 2: Server
          Logs
```

### Workflow 2: Multiple Projects

```bash
tmux new -s project1         # First project
tmux new -s project2         # Second project
Ctrl+b s                     # Switch between sessions
Ctrl+b d                     # Detach
tmux attach -t project1      # Come back later
```

### Workflow 3: SSH Work

```bash
ssh server                   # Connect to server
tmux new -s work             # Start tmux on server
# Do your work...
# Connection drops? No problem!
ssh server                   # Reconnect
tmux attach -t work          # Resume exactly where you left off
```

---

## Tips & Tricks

### 1. Name Everything!
```bash
# Name sessions
tmux new -s meaningful-name

# Rename windows
Ctrl+b ,

# Better than numbers!
```

### 2. Use Windows for Different Tasks
- Window 1: editor
- Window 2: server
- Window 3: database
- Window 4: logs

### 3. Use Panes for Related Tasks
- Editor + terminal
- Logs + monitoring
- Two config files side by side

### 4. Detach Often
```bash
Ctrl+b d    # Detach - keeps running
            # Programs continue in background
            # Attach later to resume
```

### 5. Synchronized Panes for Multiple Servers
```bash
Ctrl+b :
setw synchronize-panes on
# Type commands on all servers at once!
```

### 6. Zoom is Your Friend
```bash
Ctrl+b z    # Makes one pane fullscreen temporarily
            # Press again to un-zoom
```

### 7. Use Copy Mode to Search Logs
```bash
Ctrl+b [    # Enter copy mode
/error      # Search through terminal output
```

---

## Troubleshooting

### Problem: Can't scroll
**Solution:** Enter copy mode (`Ctrl+b [`) or use mouse (already enabled!)

### Problem: Lost in nested tmux
**Solution:** Check if `$TMUX` is set: `echo $TMUX`  
Exit nested sessions until at top level

### Problem: Panes too small
**Solution:** Resize with `Ctrl+b H/J/K/L` or zoom with `Ctrl+b z`

### Problem: Forgot which session I'm in
**Solution:** Look at status bar (shows session name on left)  
Or: `tmux display-message -p '#S'`

### Problem: Accidentally killed wrong pane
**Solution:** Can't undo 😢 Be careful with `Ctrl+b x`  
Consider using `Ctrl+d` to exit cleanly instead

---

## Your Current Setup

✅ Auto-starts with "main" session  
✅ Modern, clean status bar  
✅ 12-hour IST time format  
✅ Mouse support enabled  
✅ Vi-style navigation (h/j/k/l)  
✅ Better split commands (| and -)  
✅ Config at `~/.tmux.conf`  
✅ Reload with `Ctrl+b r`

---

## Next Steps

Now that you know the basics:

1. ✅ Practice creating and switching between windows
2. ✅ Try splitting into panes for your workflow
3. ✅ Experiment with different layouts (`Ctrl+b Space`)
4. ✅ Learn copy mode for searching logs
5. ✅ Create multiple sessions for different projects
6. ✅ Customize your config more (colors, bindings, etc)

---

## Advanced Topics for Later

- Tmux plugins (TPM - Tmux Plugin Manager)
- Custom key bindings
- Scripting tmux session creation
- Pair programming with tmux
- Integration with vim/neovim
- Custom status bar with scripts
- Tmux resurrect (save/restore sessions)

---

**You're all set! Start experimenting and tmux will become second nature.** 🚀
