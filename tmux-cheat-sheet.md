# 🚀 Tmux Complete Cheat Sheet

> **Ultimate reference guide** - Everything in one place!

---

## ⚡ Quick Start

```bash
# Start tmux (auto-starts as "main")
tmux

# Prefix key for all commands
Ctrl+b    # Press together, release, then command key

# First commands to try
Ctrl+b c      # Create window
Ctrl+b |      # Split vertical
Ctrl+b -      # Split horizontal
Ctrl+b d      # Detach
```

---

## 📖 Core Concepts

```
┌─────────────────────────────────────────────┐
│ Session (workspace)                         │
│  ├─ Window 1 (tab)                          │
│  │   ├─ Pane 1 (split)                      │
│  │   └─ Pane 2                              │
│  ├─ Window 2                                │
│  └─ Window 3                                │
└─────────────────────────────────────────────┘
```

---

## 🎯 Sessions

### Commands (Outside Tmux)

```bash
tmux                          # New session
tmux new -s name              # Named session
tmux ls                       # List sessions
tmux attach                   # Attach to last
tmux attach -t name           # Attach to session
tmux kill-session -t name     # Kill session
tmux kill-server              # Kill all
```

### Commands (Inside Tmux)

| Keys | Action |
|------|--------|
| `Ctrl+b d` | Detach |
| `Ctrl+b $` | Rename session |
| `Ctrl+b s` | Session list |
| `Ctrl+b (` | Previous session |
| `Ctrl+b )` | Next session |

---

## 🪟 Windows

| Keys | Action |
|------|--------|
| `Ctrl+b c` | Create window |
| `Ctrl+b ,` | Rename window |
| `Ctrl+b &` | Kill window |
| `Ctrl+b n` | Next window |
| `Ctrl+b p` | Previous window |
| `Ctrl+b 0-9` | Switch to window # |
| `Ctrl+b w` | Window list (interactive) |
| `Ctrl+b l` | Last window |
| `Ctrl+b f` | Find window |

---

## 📐 Panes

### Create & Kill

| Keys | Action |
|------|--------|
| `Ctrl+b \|` | Split vertical *(custom)* |
| `Ctrl+b -` | Split horizontal *(custom)* |
| `Ctrl+b x` | Kill pane |
| `Ctrl+b !` | Break pane → window |

### Navigate

| Keys | Action |
|------|--------|
| `Ctrl+b h` | Left *(custom vim)* |
| `Ctrl+b j` | Down *(custom vim)* |
| `Ctrl+b k` | Up *(custom vim)* |
| `Ctrl+b l` | Right *(custom vim)* |
| `Ctrl+b ←↑→↓` | Arrow keys |
| `Ctrl+b o` | Next pane |
| `Ctrl+b q` | Show pane numbers |
| `Ctrl+b q 0-9` | Go to pane # |

### Resize

| Keys | Action |
|------|--------|
| `Ctrl+b H` | Left *(custom)* |
| `Ctrl+b J` | Down *(custom)* |
| `Ctrl+b K` | Up *(custom)* |
| `Ctrl+b L` | Right *(custom)* |

### Layout

| Keys | Action |
|------|--------|
| `Ctrl+b z` | **Zoom toggle** |
| `Ctrl+b Space` | Cycle layouts |
| `Ctrl+b {` | Move pane left |
| `Ctrl+b }` | Move pane right |
| `Ctrl+b Ctrl+o` | Rotate panes |

---

## 📝 Copy Mode

### Enter/Exit

| Keys | Action |
|------|--------|
| `Ctrl+b [` | Enter copy mode |
| `q` or `Esc` | Exit copy mode |

### Navigation (Vi Mode)

| Keys | Action |
|------|--------|
| `h j k l` | Move cursor |
| `w` / `b` | Word forward/back |
| `Ctrl+u` / `Ctrl+d` | Page up/down |
| `g` / `G` | Top/bottom |
| `0` / `$` | Start/end of line |

### Search

| Keys | Action |
|------|--------|
| `/` | Search forward |
| `?` | Search backward |
| `n` | Next match |
| `N` | Previous match |

### Selection & Copy

| Keys | Action |
|------|--------|
| `Space` | Start selection |
| `Enter` | Copy selection & exit |
| `v` | Toggle selection mode |
| `V` | Line selection mode |
| `Ctrl+v` | Rectangle selection |

### Paste

| Keys | Action |
|------|--------|
| `Ctrl+b ]` | Paste buffer |

---

## 🖱️ Mouse Support

**Your config has mouse enabled:**

- ✅ Click panes to switch
- ✅ Click windows in status bar
- ✅ Drag borders to resize
- ✅ Scroll with wheel
- ✅ Select text (auto-copy)
- ✅ Right-click to paste

---

## ⚙️ Command Mode

```
Ctrl+b :    # Enter command mode
```

### Useful Commands

```bash
# Pane resizing
resize-pane -D 10           # Down 10 lines
resize-pane -U 10           # Up 10 lines
resize-pane -L 10           # Left 10 columns
resize-pane -R 10           # Right 10 columns
resize-pane -Z              # Zoom toggle

# Layouts
select-layout even-horizontal
select-layout even-vertical
select-layout main-horizontal
select-layout main-vertical
select-layout tiled

# Pane management
swap-pane -U                # Swap up
swap-pane -D                # Swap down
break-pane                  # Break to new window
join-pane -t :1             # Join to window 1

# Synchronized typing (type in all panes)
setw synchronize-panes on
setw synchronize-panes off

# Window management
swap-window -s 2 -t 1       # Swap windows
move-window -t 0            # Move to position 0

# Session management
rename-session myname
switch-client -t session

# Config
source-file ~/.tmux.conf    # Reload config
```

---

## 🔧 Help & Info

| Keys | Action |
|------|--------|
| `Ctrl+b ?` | List all keybindings |
| `Ctrl+b t` | Show clock |
| `Ctrl+b i` | Show pane info |
| `Ctrl+b r` | Reload config *(custom)* |

---

## 💼 Common Workflows

### Development Setup

```bash
# Start project session
tmux new -s myproject

# Window 1: Code
Ctrl+b ,              # Rename to "code"
Ctrl+b -              # Split: editor top, terminal bottom

# Window 2: Server
Ctrl+b c              # New window
Ctrl+b ,              # Rename to "server"
npm start

# Window 3: Logs
Ctrl+b c              # New window
Ctrl+b ,              # Rename to "logs"
tail -f app.log

# Detach when done
Ctrl+b d

# Resume later
tmux attach -t myproject
```

### Multiple Servers

```bash
# Create 3 panes for 3 servers
Ctrl+b |              # Split
Ctrl+b |              # Split again

# SSH to each server
ssh server1           # Left pane
ssh server2           # Middle pane
ssh server3           # Right pane

# Type on all servers at once
Ctrl+b :
setw synchronize-panes on

# Run commands on all
sudo apt update
```

### Log Monitoring

```bash
# Split into 4 panes
Ctrl+b |              # Split vertical
Ctrl+b -              # Split horizontal
Ctrl+b h              # Go left
Ctrl+b -              # Split horizontal

# Monitor different logs in each pane
tail -f /var/log/nginx/access.log
tail -f /var/log/nginx/error.log
tail -f /var/log/app.log
htop
```

---

## 🎨 Status Bar Info

**Your custom status bar shows:**

```
[Session]  Window1  Window2*  Window3     Time  Date  Hostname
  main      1 bash   2 vim     3 logs     02:30 PM  Mon 02 Nov  laptop
```

- **Left:** Session name (blue background)
- **Middle:** Windows (active in cyan)
- **Right:** Time (IST), Date, Hostname

---

## 🔥 Pro Tips

### 1. Name Your Sessions

```bash
# Instead of:
tmux    # Creates numbered session

# Do this:
tmux new -s work
tmux new -s personal
tmux new -s client-X
```

### 2. Use Zoom Liberally

```
Ctrl+b z    # Fullscreen current pane
            # Work on it
Ctrl+b z    # Back to split view
```

### 3. Master Copy Mode

```
# Quickly search logs:
Ctrl+b [    # Enter copy mode
/ERROR      # Search for "ERROR"
n           # Next match
```

### 4. Synchronized Panes for Deploy

```bash
# Deploy to multiple servers:
Ctrl+b :
setw synchronize-panes on

# Commands run on all servers
git pull
npm install
pm2 restart app
```

### 5. Quick Layouts

```
Ctrl+b Space    # Cycle through layouts
                # Keep pressing until you like it
```

### 6. Save Your Fingers

```bash
# Create aliases in ~/.bashrc
alias dev='tmux attach -t dev || tmux new -s dev'
alias work='tmux attach -t work || tmux new -s work'

# Just type:
work    # Attaches or creates
```

### 7. Detach Often

```
# SSH connection drops? No problem!
Ctrl+b d    # Detach before closing laptop
            # Tmux keeps running
            # Reconnect and resume
```

---

## 🆘 Troubleshooting

### Can't Scroll

**Problem:** Mouse wheel doesn't scroll  
**Solution:** Enter copy mode: `Ctrl+b [`  
*(Mouse scroll already enabled in your config)*

### Lost in Panes

**Problem:** Too many panes, confused  
**Solution:**
- `Ctrl+b q` - Show pane numbers
- `Ctrl+b z` - Zoom one pane
- `Ctrl+b x` - Kill pane

### Nested Tmux

**Problem:** Accidentally started tmux in tmux  
**Solution:** Check: `echo $TMUX`  
If set, you're in tmux. Exit inner session.

### Forgot Session Name

**Problem:** Which session am I in?  
**Solution:**
- Look at status bar (left side)
- Or: `tmux display-message -p '#S'`

### Config Not Loading

**Problem:** Changes don't apply  
**Solution:**
```bash
# Check file exists
ls ~/.tmux.conf

# Reload
tmux source-file ~/.tmux.conf

# Or restart tmux
tmux kill-server
tmux
```

---

## 📊 Your Custom Config

### Features

✅ Auto-starts as "main" session  
✅ 12-hour IST time format  
✅ Modern blue/cyan theme  
✅ Vi navigation (hjkl)  
✅ Better splits (| and -)  
✅ Mouse support  
✅ 5000 lines history  
✅ Windows start at 1

### Custom Bindings

| Keys | Action |
|------|--------|
| `Ctrl+b \|` | Split vertical |
| `Ctrl+b -` | Split horizontal |
| `Ctrl+b h/j/k/l` | Navigate panes |
| `Ctrl+b H/J/K/L` | Resize panes |
| `Ctrl+b r` | Reload config |

### Files

- **Config:** `~/.tmux.conf`
- **Auto-start:** `~/.bashrc`

---

## 🎓 Learning Path

### Beginner (Week 1)
- [ ] Start/attach/detach sessions
- [ ] Create and switch windows
- [ ] Basic pane splits
- [ ] Learn copy mode scrolling

### Intermediate (Week 2-3)
- [ ] Name sessions and windows
- [ ] Use zoom feature
- [ ] Copy and paste text
- [ ] Search in copy mode
- [ ] Multiple sessions

### Advanced (Month 2+)
- [ ] Synchronized panes
- [ ] Custom layouts
- [ ] Scripted session setup
- [ ] Plugin installation (TPM)
- [ ] Status bar customization

---

## 📚 Further Reading

### Official Resources
- [Tmux Manual](https://man.openbsd.org/OpenBSD-current/man1/tmux.1)
- [Tmux GitHub](https://github.com/tmux/tmux)

### Plugins
- [TPM](https://github.com/tmux-plugins/tpm) - Plugin Manager
- [tmux-resurrect](https://github.com/tmux-plugins/tmux-resurrect) - Save/restore sessions
- [tmux-continuum](https://github.com/tmux-plugins/tmux-continuum) - Auto-save

### Community
- [r/tmux](https://reddit.com/r/tmux)
- [Awesome Tmux](https://github.com/rothgar/awesome-tmux)

---

## 🎯 Quick Reference Card

```
SESSIONS:
  tmux new -s name   → Start
  tmux attach -t n   → Attach
  Ctrl+b d           → Detach
  Ctrl+b s           → List

WINDOWS:
  Ctrl+b c           → Create
  Ctrl+b ,           → Rename
  Ctrl+b n/p         → Next/Prev
  Ctrl+b 0-9         → Switch

PANES:
  Ctrl+b |/-         → Split V/H
  Ctrl+b hjkl        → Navigate
  Ctrl+b z           → Zoom
  Ctrl+b x           → Kill

COPY:
  Ctrl+b [           → Enter
  Space              → Select
  Enter              → Copy
  Ctrl+b ]           → Paste

HELP:
  Ctrl+b ?           → Commands
  Ctrl+b :           → Prompt
```

---

**🎉 You're now a tmux power user!**

*Print this cheat sheet and keep it visible while you work!*
