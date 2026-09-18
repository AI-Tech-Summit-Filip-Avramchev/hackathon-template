# AI Student Hackathon 2026

Welcome. This organisation belongs to the **AI Student Hackathon**, part of
**AI Tech Summit "Filip Avramchev" 2026** in Skopje — [techsummit.ai](https://techsummit.ai/).

~16 teams, five days, one theme:

> **Go green. Be helpful. Build something the community can use.**

You build a real project — not a slide deck — and on **22 September** your repo at 15:00 goes read-only mode.
Make sure you will commit all changes before that, codebase, documentation, recordings, everything that is part of the project.

The three best teams present again on the **Main Stage on 23 September**.

---

## How this organisation works

- **Every team member is invited to this organisation.** Accept the invitation from your email or
  from <https://github.com/AI-Tech-Summit-Filip-Avramchev> — until you accept, you cannot see
  anything here.
- **Every team gets its own repository.** Only your team can write to it. You will not see other
  teams' code, and they will not see yours.
- **This repository is the template** your team repo was created from. Read it, then work in *your*
  repo — not this one.
- **Everything you submit lives in your team repo.** There is no separate upload, no zip file, no
  email. What is pushed by the deadline is what gets judged.

**Your team repo looks like this:**

```
git@github.com:AI-Tech-Summit-Filip-Avramchev/<your-team-name>.git
```

Your mentor will tell you the exact name on day one.

---

## Part 1 — Set up git (do this on day one, once)

Do this **before** you need it. Doing it at 2am on day four is not fun.

You need a terminal:

| Your computer | Open this |
|---|---|
| **Windows** | **Git Bash** — install it from [git-scm.com/downloads](https://git-scm.com/downloads) |
| **macOS** | **Terminal** (⌘+Space, type "Terminal") |
| **Linux** | your usual terminal |

### Step 1 — Tell git who you are

Do this once. Use **the same email as your GitHub account**, so your commits show up as yours.

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

### Step 2 — Make an SSH key

An SSH key is how GitHub knows it is really you, without typing a password every time.

```bash
ssh-keygen -t ed25519 -C "your.email@example.com"
```

It asks three questions. **Press Enter for all three** (the default location, and no passphrase).

### Step 3 — Copy the key

```bash
cat ~/.ssh/id_ed25519.pub
```

It prints one long line starting with `ssh-ed25519`. **Select and copy the whole line**, including
the email at the end.

### Step 4 — Give the key to GitHub

1. Go to <https://github.com/settings/keys>
2. Click **New SSH key**
3. **Title:** anything — "my laptop" is fine
4. **Key:** paste what you copied
5. Click **Add SSH key**

### Step 5 — Check it worked

```bash
ssh -T git@github.com
```

The first time it asks `Are you sure you want to continue connecting?` — type `yes` and press Enter.

You should see:

```
Hi your-username! You've successfully authenticated, but GitHub does not provide shell access.
```

That message means **it worked**. The "does not provide shell access" part is normal, not an error.

---

## Part 2 — Get your project onto your computer

```bash
git clone git@github.com:AI-Tech-Summit-Filip-Avramchev/<your-team-name>.git
cd <your-team-name>
```

Replace `<your-team-name>` with your real repo name. You now have the project in a folder. Open that
folder in your editor (VS Code, Cursor, whatever you use).

---

## Part 3 — The loop you will repeat all week

This is 90% of the git you need. Four commands.

```bash
git pull                          # 1. get your teammates' latest work
                                  # 2. ...do your work, write code...
git add .                         # 3. mark everything you changed
git commit -m "add the bin lookup screen"   # 4. save it with a message
git push                          # 5. send it to GitHub
```

**Do this several times a day**, not once at the end. Small commits are easier to fix when something
breaks — and the judges can see you built the project rather than uploaded it.

### Writing a commit message

One short line saying what changed.

| Good | Bad |
|---|---|
| `add the bin lookup screen` | `update` |
| `fix crash when the photo is empty` | `fixes` |
| `write the README run instructions` | `asdf` |

### Always pull before you start

If two people edit at the same time, git will complain when you push. Avoid it: **`git pull` before
you start working**, every time.

---

## Part 4 — Branches (optional, but useful)

A branch is a safe place to try something without breaking what already works.

```bash
git checkout -b photo-upload      # create a branch and switch to it
                                  # ...work, then add + commit as usual...
git push -u origin photo-upload   # send the branch to GitHub
```

Then on GitHub, click **Compare & pull request** → **Create pull request** → let a teammate look →
**Merge**.

To go back to the main branch:

```bash
git checkout main
git pull
```

**You do not have to use branches.** A team of three committing carefully to `main` is completely
fine. Use branches when two people are working on the same files, or when you want to try something
risky.

---

## Part 5 — When something goes wrong

| What you see | What it means | What to do |
|---|---|---|
| `Permission denied (publickey)` | GitHub does not recognise your key | Redo Part 1, steps 2–5 |
| `Updates were rejected` | Someone pushed before you | `git pull`, fix anything it asks, then `git push` |
| `CONFLICT (content): Merge conflict in app.py` | You and a teammate edited the same lines | Open the file, you will see `<<<<<<<` and `>>>>>>>` markers. Keep the version you want, delete the markers, then `git add .` and `git commit` |
| `fatal: not a git repository` | You are in the wrong folder | `cd` into your project folder |
| You committed a password or API key | It is in the history now | **Tell your mentor immediately.** Do not just delete it in the next commit |

**Never commit secrets.** No API keys, no passwords, no `.env` file. Instead commit a `.env.example`
listing the *names* of the variables with empty values, so someone else knows what to set.

---

## How you will be judged

An AI reviewer reads your repository and scores it against the rubric below — the same way for every
team. Then the human jury reads that report, watches your demo, and decides. **The AI does not pick
the winners.** It makes sure nobody's work gets skimmed.

Everything it says must point at a real file and real lines in your repo. If it cannot find the
evidence, it cannot give you the points.

### The rubric — six things, 100 points

| Points | What we ask | In short |
|---:|---|---|
| **30** | Is it actually useful? | Can you name the person who needs this? Would they still use it next month? |
| **20** | Does the demo work? | One complete path through the app, start to finish, without someone rescuing it |
| **20** | Is the AI doing real work? | The app does something it could not do without AI — not a chat box in the corner |
| **15** | How did you build it? | Sensible structure, real commits, and honesty about what AI generated |
| **10** | Can someone else understand it? | One README: what it does, who for, how to run it, what is finished |
| **5** | Does it hold up? | Some evidence you tried to break it |

The full version, with what earns points in each one, is on the hackathon judging page — **your
mentor has the link**. Read it on **day one**, not day five.

### About your commits specifically

**This earns points:** commits spread across the build days rather than one dump on the last night,
messages that say what changed, a bug followed by the commit that fixes it, and any trace of review.
That is part of *How did you build it?* — 4 of those 15 points.

**This is recorded but never scored:** *who* committed what, how the work was split, whether
everyone's commits are linked to a GitHub account, and how many pull requests or issues you opened.

One person pushing for a pair is normal. Sharing a laptop is normal. You are not penalised for it,
and **you should not invent commits to look busier**. The jury does see your commit timeline and who
authored what, and they may ask about it on the day. Answer honestly — there is no wrong shape.

### Using AI to write your code is allowed and expected

Say so. *"We used AI to write most of the frontend so we could spend our time on the matching logic"*
is a strong answer. Pretending otherwise is a weak one — and the reviewer can usually tell.

---

## What your README should say

Your repo's README is worth **10 points**, and it is the first thing anyone reads. One page. Five
sections:

1. **What it does** — two sentences, no jargon
2. **Who it is for** — a specific person, not "everyone"
3. **How to run it** — the actual commands, and any environment variables needed
4. **What is finished and what is not** — an honest "known issues" list costs you nothing and reads
   as confidence
5. **What you would build next** with another week

Then have someone from **another team** follow your run instructions on their laptop. Whatever
breaks, fix in the README. That is the cheapest 10 points at the event.

---

## Before you submit

- [ ] The repo is accessible and the link works from someone else's account
- [ ] README says what it does, who for, and how to run it
- [ ] Someone outside your team ran it successfully
- [ ] A backup demo recording exists
- [ ] The main flow works on a phone, not just your laptop
- [ ] Your architecture diagram or sketch is in the repo
- [ ] Known issues are written down, not hidden
- [ ] Everyone can explain the whole project, not just their part
- [ ] Everything is **pushed** — run `git status` and make sure it says nothing to commit

---

## Need help?

**Ask your mentor first** — that is what they are there for, and asking on day two is much better
than asking on day four.

Event questions: [info@techsummit.ai](mailto:info@techsummit.ai)

Good luck. Build something someone will actually use.
