# Example: a week of commits into a post

A real run, unedited. The idea is made up.

- Date: 26 Oct 2026
- Claude Code 2.1.310, model claude-opus-5-5
- First Step 0.1.0, loaded from this repo as a plugin, in an empty folder with no tools

It took two turns: one question, then the first step.

---

### You

/first-step:first-step I keep thinking about a small tool that turns my week of git commits into a short update I could post, but I don't know where to start.

### Claude

Where would you post the update, and who reads it? That decides what the tool keeps from your commits and how it should sound.

For example:
- **Your team** (Slack or a standup note): concrete, a bit technical
- **Publicly** (LinkedIn, X, a blog): what you built and why it matters, without the internals
- **Just you**, as a weekly log

Or tell me something else.

### You

Publicly, on X. People who follow what I'm building, so short and plain, no internals.

### Claude

Because it's for X, the tool has to turn commit messages into a plain post of about 280 characters that says what changed for people. It shouldn't describe how the code changed.

**First step: try it by hand before building anything.** In the repo you worked in this week, run:

```sh
git log --since="7 days ago" --author="$(git config user.email)" --no-merges --pretty=format:"%ad %s%n%b" --date=short
```

Paste the output into an assistant with this prompt:

> Here are my git commits from the past week. Write one post for X, under 280 characters, for people who follow what I'm building. Use plain language and no technical internals: no file names, libraries, or refactors. Lead with the most visible thing that changed for users. Skip anything purely internal. If nothing is visible, say what I'm working toward.

**Check:** Would you post the draft as is, or after a quick edit? If yes, the idea works and the next step is a script that runs both parts. If no, what's wrong with it tells you whether to fix the prompt or your commit messages.

One gap: short messages like "fix" or "wip" give the draft little to work with. Anything private in your commits will show up in the input too, so always read the draft before posting.
