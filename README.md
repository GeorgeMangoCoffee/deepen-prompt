# deepen-prompt

A Claude skill. It makes a task deeper, not bigger.

Give it a short prompt. It reads what the task touches. It answers four questions. Then it rewrites your prompt.

The four questions come from Felix Rieseberg's ["Depth" prompt](https://felixrieseberg.com/how-to-be-more-ambitious-a-tutorial-for-humans-with-models/#depth):

1. What would a top professional do that you didn't ask for?
2. What raw material would they start from?
3. What methods and tools would they use?
4. What outside check would prove it right?

It never does the task itself. You get a rewritten prompt to copy.

## Install

### Claude desktop app and claude.ai (chat)

1. Download [`deepen-prompt.zip`](deepen-prompt.zip) from this repo.
2. Open Claude. Go to **Settings → Capabilities**.
3. Turn on **Code execution and file creation**. Skills need it.
4. Under **Skills**, click **Upload skill**.
5. Pick `deepen-prompt.zip`.
6. Check that **deepen-prompt** is switched on.

It syncs to the desktop app and the web.

### Claude Code (terminal, or the desktop app's Code tab)

Clone the repo. Then link the skill folder.

Windows (PowerShell, as admin or with Developer Mode):

```powershell
git clone https://github.com/GeorgeMangoCoffee/deepen-prompt C:\dev\deepen-prompt
New-Item -ItemType SymbolicLink -Path "$HOME\.claude\skills\deepen-prompt" -Target "C:\dev\deepen-prompt\deepen-prompt"
```

macOS or Linux:

```bash
git clone https://github.com/GeorgeMangoCoffee/deepen-prompt ~/deepen-prompt
ln -s ~/deepen-prompt/deepen-prompt ~/.claude/skills/deepen-prompt
```

Start a new session. Type `/deepen-prompt` to check it loads.

## Use

Say "deepen this" plus your prompt. In Claude Code you can also type `/deepen-prompt <prompt>`.

Short, vague tasks work best. Precise tasks gain little.

### Examples

```text
Deepen this: make the member portal load faster
```

Expect real timings and query plans, not guesses. Proof: a before and after measurement.

```text
Deepen this: check the offload runner is reliable
```

Expect a start from the runner logs and failed jobs. Expect kill tests, like a reboot mid-job. Proof: a job that survives a restart.

```text
Deepen this: write this week's newsletter
```

Expect a start from the stream transcripts, not old summaries. Proof: quotes in the speaker's own words.

```text
Deepen this: tidy up my system guide
```

Expect each section checked against real paths. Proof: every listed path exists.

```text
Deepen this: should we raise our prices?
```

Expect churn data, competitor prices and a small test group. Proof: a pre-set target the test must hit.

### Bad fits

- "Rename this variable." It's already exact.
- "What time is it in New York?" That's a fact, not a task.

### Did it work?

Compare the rewrite with your prompt. It should name files, data or a check you missed. If it only adds big words, the task was too narrow.

## What you get

1. The decision, the field and the expert role.
2. Four short lists, one per question.
3. The rewritten prompt in a code block.

## Where it reads from

In chat it reads attached files, project knowledge and connected tools. In Claude Code it reads your working folder. With nothing to read, it says so and goes on.

## Rebuild the zip

After you edit `deepen-prompt/SKILL.md`, rebuild the zip. Run this in the repo folder. It works on Windows 10+, macOS and Linux:

```text
tar -a -c -f deepen-prompt.zip deepen-prompt
```

Avoid `Compress-Archive` on Windows PowerShell 5. It can write backslash paths that the upload rejects.

Then upload it again in Claude.

## Credit

The Depth prompt is by [Felix Rieseberg](https://felixrieseberg.com/).
