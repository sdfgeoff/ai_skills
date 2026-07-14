---
name: zenity
description: Use zenity to notify the user or request user input from the desktop during long-running agent work, especially when a command-line loop or goal-directed task is blocked on a human decision.
---

# Zenity Desktop Prompts

Use `zenity` only when a normal chat question is likely to be missed or the agent is blocked while working in a loop.

Common patterns:

```bash
zenity --info --title="Codex needs attention" --text="The task is paused and needs your input."
```

```bash
answer=$(zenity --entry --title="Codex question" --text="Which option should I use?")
```

```bash
if zenity --question --title="Codex confirmation" --text="Proceed with the next step?"; then
  echo yes
else
  echo no
fi
```

Keep prompts short and specific. After using zenity, report the user-visible result back in chat.
