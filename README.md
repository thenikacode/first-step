# First Step

[![License: MIT](https://img.shields.io/badge/license-MIT-blue)](LICENSE) [![Follow @thenikacode on X](https://img.shields.io/badge/follow-%40thenikacode-000000?logo=x&logoColor=white)](https://x.com/thenikacode)

**Give your agent a vague idea. It asks one useful question at a time, then hands you a small first step you can check.**

![A real First Step run in Claude Code on a made-up idea. You: I keep thinking about a small tool that turns my week of git commits into a short update I could post, but I don't know where to start. Claude asks one question: where would you post the update, and who reads it? It suggests your team, publicly, or just you. You answer: publicly, on X, short and plain. Claude gives the first step: try it by hand before building anything. Run git log for the past week, paste the output into an assistant with a short prompt for one post under 280 characters, then check whether you would post the draft as is or after a quick edit.](docs/first-step-dialog.png)

First Step is a skill for Claude Code and Codex. Each turn, it asks the question whose answer would most change your first piece of work. It stops once it can name a small step and how you'll check it. In the run above it asked one question, then gave the first step ([full transcript](examples/weekly-commit-update.md)).

## Install

In Claude Code 2.1.275 or later:

```
/plugin install first-step --marketplace thenikacode/first-step
```

<details>
<summary>Older Claude Code versions</summary>

```
/plugin marketplace add thenikacode/first-step
/plugin install first-step@first-step
```

</details>

With the skills CLI, for Claude Code, Codex and other agents that read skills:

```
npx skills add thenikacode/first-step -g
```

In Codex by hand, copy `skills/first-step` into `~/.agents/skills/first-step`:

```
git clone https://github.com/thenikacode/first-step
mkdir -p ~/.agents/skills && cp -R first-step/skills/first-step ~/.agents/skills/
```

## Use

Type the command, then your idea in your own words:

```
/first-step:first-step <your idea>
```

The command depends on how you installed it:

- Claude Code plugin: `/first-step:first-step`
- skills CLI, in Claude Code: `/first-step`
- Codex: `$first-step`

## What it does

The skill is one Markdown file of instructions, [SKILL.md](skills/first-step/SKILL.md). It tells your agent to:

- start from what you've told it and, when it can, from the project you have open;
- ask one question per turn, with two or three suggested answers when that helps, and take an answer in your own words;
- tell you when two of your requirements conflict, and ask which one comes first;
- stop asking once it can name a small first step and a way to check it, with no fixed number of questions;
- keep the result short, at most about 200 words for a small task;
- skip the questions when your request is already clear;
- write an assignment you can paste into another assistant, if you want to carry on there.

## What it doesn't do

- It has no memory between chats. Each run starts from the conversation you're in.
- It doesn't promise that your plan or business will work.
- Its instructions say that planning with it isn't permission to build, publish, buy or message anyone. The skill can't enforce that: your agent's own permissions decide what it can do.
- It isn't meant for a clear task, a small edit, a translation or a factual question.
- Answers change from one model to another, and from one run to the next.

## Example

[A week of commits into a post](examples/weekly-commit-update.md) is a real run in Claude Code 2.1.310 on 26 Oct 2026, unedited. The idea is made up. It took one question, then the first step and its check.

## FAQ

### Isn't this just a prompt?

Yes, a long one in a single file, so you can read all of it before you install it. Claude Code and Codex load the same file, and you don't retype it each time. I haven't compared it with a good hand-written prompt.

### It asked a bad question

[Open an issue](https://github.com/thenikacode/first-step/issues/new) and paste the conversation, for example when it asked two things at once or asked for something you'd already told it. Take out anything private first.

## License

MIT. Made by [Nika Code](https://github.com/thenikacode) with Claude Code and Codex. Contributions are welcome: see [CONTRIBUTING.md](CONTRIBUTING.md).

Follow the build on X: [@thenikacode](https://x.com/thenikacode).

Not affiliated with Anthropic or OpenAI.
