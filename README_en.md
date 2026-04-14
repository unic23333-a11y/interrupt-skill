# Interrupt Skill

> Let AI understand your "interruptions" — intelligently decide whether to modify the current task or start a new one.

---

## What is this

Have you ever遇到过 these situations when using an AI assistant:

- AI is generating something, and you suddenly want to add or modify
- AI has gone off track, but you don't want to wait for it to finish
- You want to start a new task, but don't want to lose progress on the current one

「Interrupt Skill」is designed to solve these problems.

---

## Core Features

### 1. Intelligent Detection

AI automatically判断 your words:
- **Related to current task** → Modify/supplement current task
- **Unrelated to current task** → Answer directly, without interrupting

### 2. Modify Current Task

When AI is generating, your words are intelligently parsed:

| You say | AI understands | Action |
|---------|---------------|--------|
| "Add Python to my resume" | Modification | Modify directly, continue generating |
| "Add a portfolio section too" | Addition | Pause, add, continue |
| "No wait, I meant..." | Correction | Pause, update context, regenerate |
| "Help me check something first" | New task | Suspend current, start new task |

### 3. Multi-Task Queue

Manage up to 3 tasks simultaneously:

```
Queue full? → Prompt to complete one first
Queue not full? → Suspend current, start new task
```

---

## Trigger Conditions

Triggered when **any** of the following is met:

| Condition | Description |
|-----------|-------------|
| AI is executing a task | Generating/Thinking/Searching → Any input triggers |
| Starts with a comma | English`,` Chinese`，` Japanese`、` etc. |

---

## Usage

### Scenario A: When AI is executing a task

Just say what you want — AI will automatically judge:

```
AI: Analyzing this data report...
You: Move the conclusion to the front first
AI: [Understood as modification] → Adjust structure → Continue analyzing

---

AI: Writing a proposal
You: Wait, first confirm who the target users are
AI: [Understood as pause] → Stop and wait for you
```

### Scenario B: Anytime

Start with a **comma** (English`,`, Chinese`，`, Japanese`、` etc.) to activate interrupt mode:

```
You: , help me check tomorrow's weather
AI: [Suspend current task] → Start checking weather

---

You: , there's something urgent I need to handle
AI: [Suspend] → Handle new task
```

---

## Notes

1. **Queue limit: 3 tasks** — Will prompt when queue is full
2. **Regeneration after modification** — Not in-place editing, regenerates full content
3. **Context is preserved** — Won't lose progress when switching tasks

---

## Problems Solved

| Problem | Solution |
|---------|----------|
| AI going wrong but must wait | Interrupt anytime during generation |
| New task might disrupt old task | Background suspend, tasks preserved |
| Context pollution | Task isolation, no interference |

---

## Technical Background

This Skill fills a gap in OpenClaw — the official implementation of "interrupt during generation" hasn't been realized (see [OpenClaw Feature Request #13675](https://github.com/openclaw/openclaw/issues/13675)).

References:
- OpenAI Realtime API interruption mechanism
- NVIDIA PersonaPlex full-duplex conversation
- Microsoft Research: Lost in Multi-Turn Conversation

---

## Installation

Place this folder in OpenClaw's skills directory.

---

## Author

Henry Qian

---

## License

MIT
