[Hackathon overview](README.md) · [Git setup and workflow](git.md) · [SSH setup](ssh.md) · [Redeem your OpenAI code](openai-redemption.md)

# Git setup and everyday workflow

Do this **before** you need it. Doing it at 2am on day four is not fun.

You need a terminal:

| Your computer | Open this |
|---|---|
| **Windows** | **Git Bash** — install it from [git-scm.com/downloads](https://git-scm.com/downloads) |
| **macOS** | **Terminal** (⌘+Space, type "Terminal") |
| **Linux** | your usual terminal |

## Set your commit identity

Do this once. Use **the same email as your GitHub account**, so your commits show up as yours.

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

## Clone your team repository

Complete [SSH setup](ssh.md) first.

```bash
git clone git@github.com:AI-Tech-Summit-Filip-Avramchev/<your-team-name>.git
cd <your-team-name>
```

Replace `<your-team-name>` with your real repo name. You now have the project in a folder. Open that
folder in your editor (VS Code, Cursor, whatever you use).

---

## Your everyday workflow

Run these commands from your project folder.

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

If two people edit at the same time, git will complain when you push. Reduce conflicts by running **`git pull` before you start working**. Conflicts can still happen; ask your mentor if you are unsure how to resolve one.

---

## Branches (optional)

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

## Troubleshooting

| What you see | What it means | What to do |
|---|---|---|
| `Permission denied (publickey)` | GitHub does not recognise your key | Follow the [SSH setup guide](ssh.md) |
| `Updates were rejected` | Someone pushed before you | `git pull`, fix anything it asks, then `git push` |
| `CONFLICT (content): Merge conflict in app.py` | You and a teammate edited the same lines | Open the file, you will see `<<<<<<<` and `>>>>>>>` markers. Keep the version you want, delete the markers, then `git add .` and `git commit` |
| `fatal: not a git repository` | You are in the wrong folder | `cd` into your project folder |
| You committed a password or API key | It is in the history now | **Tell your mentor immediately.** Do not just delete it in the next commit |

**Never commit secrets.** No API keys, no passwords, no `.env` file. Instead commit a `.env.example`
listing the *names* of the variables with empty values, so someone else knows what to set.

---

[Hackathon overview](README.md) · [Git setup and workflow](git.md) · [SSH setup](ssh.md) · [Redeem your OpenAI code](openai-redemption.md)

