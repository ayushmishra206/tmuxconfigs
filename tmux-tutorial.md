# 🎯 Tmux Hands-On Tutorial

> Learn tmux by doing! Follow these exercises step by step.

---

## 📚 Table of Contents

- [Exercise 1: First Steps](#exercise-1-first-steps-5-minutes)
- [Exercise 2: Working with Panes](#exercise-2-working-with-panes-10-minutes)
- [Exercise 3: Real World - Web Dev](#exercise-3-real-world-scenario---web-dev-15-minutes)
- [Exercise 4: Copy Mode Mastery](#exercise-4-copy-mode-mastery-10-minutes)
- [Exercise 5: Multiple Sessions](#exercise-5-multiple-sessions-10-minutes)
- [Exercise 6: Advanced - Synchronized Panes](#exercise-6-advanced---synchronized-panes-5-minutes)
- [Challenge: Create Your Ideal Setup](#challenge-create-your-ideal-setup)

---

## Exercise 1: First Steps (5 minutes)

**Goal:** Get comfortable with basic tmux

### Step 1: Start tmux
```bash
tmux
```
✅ You should see a status bar at the bottom  
✅ It shows "main" on the left (your session name)  
✅ Time on the right in IST format

### Step 2: Create a new window
```
Press: Ctrl+b then c
```
✅ Notice the status bar changed  
✅ You now see "1 bash" and "2 bash"  
✅ The active window is highlighted in cyan

### Step 3: Switch between windows
```
Press: Ctrl+b then 1     # switch to window 1
Press: Ctrl+b then 2     # switch to window 2
Press: Ctrl+b then n     # next window
Press: Ctrl+b then p     # previous window
```

### Step 4: Rename a window
```
Press: Ctrl+b then ,
Type: "editor"
Press: Enter
```
✅ Window name changed from "bash" to "editor"

### Step 5: Detach from tmux
```
Press: Ctrl+b then d
```
✅ You're back in regular terminal  
✅ But tmux is still running in background!

### Step 6: List sessions
```bash
tmux ls
```
✅ You should see: `main: 2 windows ...`

### Step 7: Reattach
```bash
tmux attach -t main
```
✅ You're back where you left off!  
✅ All your windows are still there

### ✅ Exercise 1 Complete!

---

## Exercise 2: Working with Panes (10 minutes)

**Goal:** Learn to split your screen and work with multiple terminals

### Step 1: Start fresh
```bash
tmux kill-server
tmux new -s practice
```

### Step 2: Split vertically (side by side)
```
Press: Ctrl+b then |
```
✅ Screen is now split in two  
✅ Left and right panes

### Step 3: Navigate between panes
```
Press: Ctrl+b then h     # move left
Press: Ctrl+b then l     # move right
```
Practice moving back and forth a few times

### Step 4: Split horizontally in right pane
```
Make sure you're in the right pane
Press: Ctrl+b then -
```
✅ Right pane is now split top/bottom  
✅ You have 3 panes total

### Step 5: Navigate all panes
```
Press: Ctrl+b then h     # left pane
Press: Ctrl+b then l     # right panes
Press: Ctrl+b then k     # top right
Press: Ctrl+b then j     # bottom right
```

### Step 6: Do something in each pane
```bash
# Left pane:
ls -la

# Top right:
htop        # or top

# Bottom right:
echo "Hello from pane 3"
```

### Step 7: Zoom a pane
```
Press: Ctrl+b then z
```
✅ Current pane goes fullscreen  
✅ Press `Ctrl+b z` again to un-zoom

### Step 8: Resize panes
```
Go to left pane: Ctrl+b then h
Make it bigger:  Ctrl+b then L (capital L)
```
Press multiple times to resize more

### Step 9: Kill a pane
```
Go to bottom right: Ctrl+b then j then j
Press: Ctrl+b then x
Press: y (to confirm)
```
✅ Pane is closed  
✅ Remaining panes expand

### ✅ Exercise 2 Complete!

---

## Exercise 3: Real World Scenario - Web Dev (15 minutes)

**Goal:** Set up a realistic development environment

### Step 1: Create a project session
```bash
tmux new -s webapp
```

### Step 2: Rename first window to "code"
```
Press: Ctrl+b then ,
Type: code
Press: Enter
```

### Step 3: Create a temp project directory
```bash
mkdir ~/tmux-practice
cd ~/tmux-practice
echo "console.log('Hello World');" > app.js
```

### Step 4: Split for editor and terminal
```
Press: Ctrl+b then -
```
```bash
# Top pane:
cat app.js

# Bottom pane:
echo "This is my terminal"
```

### Step 5: Create a second window for "server"
```
Press: Ctrl+b then c
Press: Ctrl+b then ,
Type: server
Press: Enter
```
```bash
echo "Server would run here..."
watch -n 1 date    # shows updating time
```

### Step 6: Create a third window for "logs"
```
Press: Ctrl+b then c
Press: Ctrl+b then ,
Type: logs
```
```bash
# If you have system logs:
tail -f /var/log/syslog

# Or use:
dmesg -w
```

### Step 7: Navigate your workspace
```
Press: Ctrl+b then 1    # code window
Press: Ctrl+b then 2    # server window
Press: Ctrl+b then 3    # logs window
```
✅ You now have a complete dev environment!

### Step 8: View window list
```
Press: Ctrl+b then w
```
✅ Shows all windows with previews  
✅ Use arrow keys to select, Enter to switch

### Step 9: Detach and resume later
```
Press: Ctrl+b then d

# Do something else...
# Come back:
tmux attach -t webapp
```
✅ Everything is exactly as you left it!

### ✅ Exercise 3 Complete!

---

## Exercise 4: Copy Mode Mastery (10 minutes)

**Goal:** Learn to scroll and copy text in tmux

### Step 1: Generate some output
```bash
for i in {1..100}; do echo "Line $i"; done
```
✅ Screen fills with lines  
✅ Can't scroll back normally

### Step 2: Enter copy mode
```
Press: Ctrl+b then [
```
✅ You're now in copy mode  
✅ Notice cursor appears

### Step 3: Navigate with vim keys
```
Press: k k k k k    # move up
Press: j j j j j    # move down
Press: h            # move left
Press: l            # move right
```

### Step 4: Page up and down
```
Press: Ctrl+u       # half page up
Press: Ctrl+d       # half page down
```

### Step 5: Jump to top and bottom
```
Press: g            # go to top
Press: G            # go to bottom
```

### Step 6: Search for text
```
Press: /
Type: Line 50
Press: Enter
```
✅ Jumps to "Line 50"

```
Press: n            # next match
Press: N            # previous match
```

### Step 7: Copy some text
```
Navigate to "Line 20"
Press: Space        # start selection
Press: j j j j      # select 5 lines
Press: Enter        # copy and exit
```

### Step 8: Paste the text
```
Press: Ctrl+b then ]
```
✅ The 5 lines are pasted!

### Step 9: Practice scrolling with mouse
Just use your mouse wheel to scroll
✅ Mouse support is already enabled!

### ✅ Exercise 4 Complete!

---

## Exercise 5: Multiple Sessions (10 minutes)

**Goal:** Manage multiple projects with different sessions

### Step 1: Create first project session
```bash
tmux new -s project-A
echo "Working on Project A"
```

### Step 2: Detach and create second session
```
Press: Ctrl+b then d
```
```bash
tmux new -s project-B
echo "Working on Project B"
```

### Step 3: Create a third session
```
Press: Ctrl+b then d
```
```bash
tmux new -s personal
echo "Personal stuff"
```

### Step 4: List all sessions
```
Press: Ctrl+b then d
```
```bash
tmux ls
```
✅ You should see all three sessions

### Step 5: Switch between sessions
```
Press: Ctrl+b then s
```
✅ Shows list of sessions  
✅ Use arrow keys to select  
✅ Press Enter to switch

### Step 6: Quick switch with commands
```
Press: Ctrl+b then d
```
```bash
tmux attach -t project-A
# Work on A...

# Detach and switch
tmux attach -t project-B
# Work on B...
```

### Step 7: Kill a session
```bash
tmux kill-session -t personal
tmux ls
```
✅ Only project-A and project-B remain

### Step 8: Clean up
```bash
tmux kill-server
```
✅ All sessions are gone

### ✅ Exercise 5 Complete!

---

## Exercise 6: Advanced - Synchronized Panes (5 minutes)

**Goal:** Type commands on multiple panes/servers at once

### Step 1: Create layout
```bash
tmux
```
```
Press: Ctrl+b then |    # split vertical
Press: Ctrl+b then |    # split again
```
✅ You now have 3 vertical panes

### Step 2: Enable synchronization
```
Press: Ctrl+b then :
Type: setw synchronize-panes on
Press: Enter
```

### Step 3: Type in all panes at once
```bash
echo "This appears in all panes!"
ls
date
```
✅ Same commands run in all 3 panes!

### Step 4: Disable synchronization
```
Press: Ctrl+b then :
Type: setw synchronize-panes off
Press: Enter
```
✅ Back to normal - each pane independent

**Use case:** Running the same command on multiple servers!

### ✅ Exercise 6 Complete!

---

## Challenge: Create Your Ideal Setup

Now create your own workspace! Here's a template:

### 1. Create a session with your project name
```bash
tmux new -s myproject
```

### 2. Window 1: Code (split into editor + terminal)
```
Ctrl+b ,    # rename to "code"
Ctrl+b -    # split horizontal
```

### 3. Window 2: Server/Services
```
Ctrl+b c    # new window
Ctrl+b ,    # rename to "server"
```

### 4. Window 3: Monitoring
```
Ctrl+b c    # new window
Ctrl+b ,    # rename to "monitor"
Ctrl+b |    # split vertical
# Left: htop
# Right: logs
```

### 5. Save your work by detaching
```
Ctrl+b d
```

### 6. Come back tomorrow
```bash
tmux attach -t myproject
```

---

## 💡 Tips From Practice

### 1. Name everything!
```bash
# Sessions
tmux new -s meaningful-name

# Windows
Ctrl+b , # to rename

# Better than numbers!
```

### 2. Zoom is your friend
```
Ctrl+b z    # Focus on one pane
Ctrl+b z    # Return to normal
```

### 3. Don't fight the mouse
- Click to switch panes
- Drag to resize
- Mouse wheel to scroll

### 4. Learn copy mode gradually
1. Start with just scrolling
2. Add searching next
3. Then copying/pasting

### 5. Start simple
- One session
- Few windows
- Split when needed
- Don't over-complicate!

### 6. Use your custom bindings
- `|` and `-` are easier than `%` and `"`
- `h/j/k/l` is natural if you know vim

### 7. Detach often
- Keeps work safe
- Easy to resume
- No lost work on SSH drops

---

## 🎓 What's Next?

**Now you know tmux basics!** Keep practicing and it'll become natural.

### Advanced topics to explore later:
- Tmux plugins (tmux-resurrect, tmux-continuum)
- Custom status bar scripts
- Tmux + Vim integration
- Scripting session creation
- Pair programming setup

### But for now - just use what you learned!
- Create sessions for your projects
- Split panes for your workflow
- Enjoy your new superpower!

---

## ✅ All Exercises Complete! 

**You're now a tmux user!** 🎉

---

### Quick Practice Reminder

```bash
# Daily workflow:
tmux new -s work        # Start work session
Ctrl+b c                # New window
Ctrl+b |                # Split panes
# ... do your work ...
Ctrl+b d                # Detach

# Come back:
tmux attach -t work     # Resume where you left off
```

**Keep this guide handy and practice a little each day!**
