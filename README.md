# Socratic Tutor - Learn Anything

An agentic tutoring experiment using a modified version Jane Street's [socratic-tutor skill](https://github.com/janestreet/agent_skills/tree/master/socratic-tutor) for the purpose of learning anything.

It contains two [Claude Code](https://claude.com/claude-code) skills and the lesson files they work with:

- **`lesson`** writes a lesson file for a topic, in a fixed template.
- **`socratic-tutor`** teaches you a topic by asking questions instead of lecturing, and tracks how well you know each part of it. Status of lesson is preserved between sessions.

### 1. Create a lesson

Ask for a lesson on a narrow topic:

```
/lesson het perfectum
```

This writes `lessons/het-perfectum.md`. A lesson has 4-10 numbered key points, ordered from basic to advanced, each with 3-5 examples.

### 2. Study the lesson

```
teach me lessons/het-perfectum.md
```

The tutor then:

1. Turns each numbered key point into a subskill.
2. Asks 3-5 diagnostic questions to place your starting level.
3. Shows a skill map and proposes where to start.
4. Asks one question at a time. When you are wrong, it asks a narrower question rather than giving the answer.
5. Re-tests earlier subskills without warning, and lowers a level if you fail.
6. Runs a final assessment once every subskill reaches the target level.

Each subskill is scored from 0 to 5:

| Level | Meaning                               |
| ----- | ------------------------------------- |
| 0     | Unaware                               |
| 1     | Heard of it                           |
| 2     | Can follow along                      |
| 3     | Can do with help                      |
| 4     | Can do independently (default target) |
| 5     | Can teach it and handle edge cases    |

A level only goes up after two or more independent correct answers, at least one of them given without a recent hint.

### 3. Continue later

Progress is saved automatically to `progress/<lesson-name>.md`: the skill map, open misconceptions, material already covered, and a session log. Say `resume` in a later session to pick up where you stopped.

### Commands during a session

| Command               | Effect                                          |
| --------------------- | ----------------------------------------------- |
| `show progress`       | Show the skill map                              |
| `harder` / `easier`   | Adjust difficulty                               |
| `just tell me`        | Get the answer to the current question directly |
| `save state`          | Write the progress file now                     |
| `resume` / `continue` | Load saved progress for a topic                 |
| `reset progress`      | Delete a topic's progress and start again       |

## License

[MIT](LICENSE)

