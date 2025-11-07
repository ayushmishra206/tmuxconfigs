# 📚 Tmux Documentation Collection

> Complete guide to mastering tmux - from basics to advanced workflows

---

## 📖 Available Guides

### 1. [Tmux Basics - Complete Guide](./tmux-basics.md) 📘
**Best for:** Understanding tmux from the ground up

**What's inside:**
- What is tmux and why use it?
- Core concepts (sessions, windows, panes)
- Complete command reference
- Common workflows
- Tips, tricks, and troubleshooting
- Your custom config explanation

**Read this:** When you're starting fresh or want to understand the big picture

---

### 2. [Quick Reference Card](./tmux-quick-reference.md) 📋
**Best for:** Quick lookups while working

**What's inside:**
- All commands in organized tables
- Session, window, and pane management
- Copy mode reference
- Mouse support features
- Common patterns
- Survival guide

**Use this:** Print it! Keep it visible while learning. Perfect for "what was that command again?"

---

### 3. [Hands-On Tutorial](./tmux-tutorial.md) 🎯
**Best for:** Learning by doing

**What's inside:**
- 6 progressive exercises
- Step-by-step instructions
- Real-world scenarios
- Practice challenges
- Tips from experience

**Start here:** If you prefer hands-on learning. Follow exercises 1-6 in order.

---

### 4. [Complete Cheat Sheet](./tmux-cheat-sheet.md) 🚀
**Best for:** Comprehensive reference

**What's inside:**
- Everything in one place
- Quick start guide
- All commands organized
- Workflows and examples
- Pro tips
- Learning path

**Use this:** As your go-to reference once you know the basics

---

## 🎓 Recommended Learning Path

### Day 1: Get Started
1. Read: [Quick Reference - Introduction](./tmux-quick-reference.md#sessions)
2. Do: [Exercise 1: First Steps](./tmux-tutorial.md#exercise-1-first-steps-5-minutes)
3. Practice: Create a session, make windows, detach/attach

### Day 2: Master Panes
1. Do: [Exercise 2: Working with Panes](./tmux-tutorial.md#exercise-2-working-with-panes-10-minutes)
2. Practice: Split your terminal for real work

### Day 3: Real Workflow
1. Do: [Exercise 3: Web Dev Scenario](./tmux-tutorial.md#exercise-3-real-world-scenario---web-dev-15-minutes)
2. Create your own project setup

### Week 1: Advanced Features
1. Do: [Exercise 4: Copy Mode](./tmux-tutorial.md#exercise-4-copy-mode-mastery-10-minutes)
2. Do: [Exercise 5: Multiple Sessions](./tmux-tutorial.md#exercise-5-multiple-sessions-10-minutes)
3. Read: [Common Workflows](./tmux-basics.md#common-workflows)

### Week 2+: Power User
1. Do: [Exercise 6: Synchronized Panes](./tmux-tutorial.md#exercise-6-advanced---synchronized-panes-5-minutes)
2. Read: [Pro Tips](./tmux-cheat-sheet.md#-pro-tips)
3. Customize your config further

---

## 🔍 Quick Find

### I want to...

**Learn tmux from scratch**
→ [Tmux Basics Guide](./tmux-basics.md)

**Look up a command**
→ [Quick Reference Card](./tmux-quick-reference.md)

**Practice with examples**
→ [Hands-On Tutorial](./tmux-tutorial.md)

**Have everything in one place**
→ [Complete Cheat Sheet](./tmux-cheat-sheet.md)

**Understand sessions vs windows vs panes**
→ [Core Concepts](./tmux-basics.md#core-concepts)

**Set up a development environment**
→ [Exercise 3](./tmux-tutorial.md#exercise-3-real-world-scenario---web-dev-15-minutes)

**Copy and paste text**
→ [Copy Mode](./tmux-quick-reference.md#-copy-mode-scroll--copy)

**Type on multiple servers at once**
→ [Synchronized Panes](./tmux-tutorial.md#exercise-6-advanced---synchronized-panes-5-minutes)

**Fix a problem**
→ [Troubleshooting](./tmux-basics.md#troubleshooting)

---

## 💡 Essential Commands

### The Absolute Basics
```bash
# Start tmux
tmux

# Prefix key (start of all commands)
Ctrl+b

# Detach (keeps tmux running)
Ctrl+b d

# Reattach
tmux attach
```

### Most Used Commands
```
Ctrl+b c        Create window
Ctrl+b n/p      Next/previous window
Ctrl+b |        Split vertical
Ctrl+b -        Split horizontal
Ctrl+b h/j/k/l  Navigate panes (vim style)
Ctrl+b z        Zoom pane
Ctrl+b [        Scroll mode
```

---

## 📁 Your Setup

### Configuration
- **File:** `~/.tmux.conf`
- **Features:** Modern theme, IST time, mouse support, vim navigation
- **Reload:** `Ctrl+b r` or `tmux source-file ~/.tmux.conf`

### Auto-Start
- **File:** `~/.bashrc`
- **Behavior:** Auto-starts as "main" session
- **Disable:** Comment out the tmux auto-start lines

### Status Bar
```
[Session]  Window1  Window2*  Window3     Time  Date  Hostname
  main      1 bash   2 vim     3 logs     02:30 PM  Mon 02 Nov  laptop
```

---

## 🎯 Goals by Skill Level

### Beginner Goals
- [ ] Start and attach to sessions
- [ ] Create and name windows
- [ ] Split into panes
- [ ] Navigate with h/j/k/l
- [ ] Use zoom feature
- [ ] Detach and reattach

### Intermediate Goals
- [ ] Manage multiple sessions
- [ ] Use copy mode for scrolling
- [ ] Search text in copy mode
- [ ] Copy and paste between panes
- [ ] Customize layouts
- [ ] Create named sessions for projects

### Advanced Goals
- [ ] Synchronized panes for multi-server management
- [ ] Script session creation
- [ ] Custom key bindings
- [ ] Install and use plugins
- [ ] Integrate with development workflow
- [ ] Pair programming setup

---

## 🔗 External Resources

### Official
- [Tmux GitHub](https://github.com/tmux/tmux)
- [Tmux Manual](https://man.openbsd.org/OpenBSD-current/man1/tmux.1)

### Community
- [r/tmux Subreddit](https://reddit.com/r/tmux)
- [Awesome Tmux](https://github.com/rothgar/awesome-tmux)

### Plugins
- [TPM - Plugin Manager](https://github.com/tmux-plugins/tpm)
- [tmux-resurrect](https://github.com/tmux-plugins/tmux-resurrect) - Save sessions
- [tmux-continuum](https://github.com/tmux-plugins/tmux-continuum) - Auto-save

---

## 📊 Document Overview

| Document | Length | Best For | Format |
|----------|--------|----------|--------|
| Basics Guide | Long | Learning & Reference | Detailed explanations |
| Quick Reference | Medium | Lookup & Daily Use | Tables & lists |
| Tutorial | Medium | Practice | Step-by-step |
| Cheat Sheet | Long | Comprehensive Reference | Everything in one |

---

## 🎨 Printing Tips

### For Daily Use
Print the [Quick Reference Card](./tmux-quick-reference.md) and keep it visible at your desk.

### For Learning
Print the [Tutorial](./tmux-tutorial.md) and work through exercises with pen/paper notes.

### For Reference
Keep the [Cheat Sheet](./tmux-cheat-sheet.md) as a PDF on your second monitor.

---

## 💬 Common Questions

### Q: Which document should I read first?
**A:** If you're completely new, start with the [Tutorial](./tmux-tutorial.md) - do Exercise 1 and 2. Then use the [Quick Reference](./tmux-quick-reference.md) for lookups.

### Q: I keep forgetting commands, what should I do?
**A:** Print the [Quick Reference Card](./tmux-quick-reference.md) and keep it visible. Muscle memory takes 1-2 weeks.

### Q: How do I customize tmux more?
**A:** Read the config explanations in [Basics Guide](./tmux-basics.md) and check the Advanced Topics section.

### Q: Can I use tmux for remote work?
**A:** Yes! Tmux is perfect for SSH. See [Workflow 3 in Basics](./tmux-basics.md#workflow-3-ssh-work).

### Q: What's the difference between a session and window?
**A:** See [Core Concepts](./tmux-basics.md#core-concepts). TL;DR: Session = workspace, Window = tab, Pane = split.

---

## 🚀 Start Now!

### 30-Second Quick Start
```bash
# Open terminal (tmux auto-starts as "main")
Ctrl+b c        # Create new window
Ctrl+b |        # Split vertically
Ctrl+b h/l      # Switch between panes
# You're using tmux! 🎉
```

### 5-Minute First Session
1. Open terminal
2. Follow [Exercise 1](./tmux-tutorial.md#exercise-1-first-steps-5-minutes)
3. You'll understand sessions, windows, and detaching

### 1-Hour Deep Dive
1. Read [Core Concepts](./tmux-basics.md#core-concepts)
2. Complete [Exercises 1-3](./tmux-tutorial.md)
3. Try creating your own project setup
4. Keep [Quick Reference](./tmux-quick-reference.md) open

---

## 📝 Notes

- All guides are in **Markdown format** for easy reading on GitHub or in editors
- Commands are formatted in `code blocks` for clarity
- Tables organize information for quick scanning
- Emojis help with visual navigation
- Cross-references link related topics

---

## ✨ Happy tmuxing!

Remember: **Start simple, practice daily, master gradually.**

The key is not to memorize everything at once - just learn the basics and build from there. Keep the Quick Reference handy and you'll be a tmux pro in no time!

---

*Last updated: 2025-11-02*  
*Your config: Modern theme, IST time, Vim navigation, Mouse support*
