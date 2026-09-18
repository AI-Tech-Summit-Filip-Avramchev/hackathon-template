[Hackathon overview](README.md) · [Git setup and workflow](git.md) · [SSH setup](ssh.md) · [Redeem your OpenAI code](openai-redemption.md)

# Connect to GitHub with SSH

Use the terminal from the [Git setup guide](git.md). If this computer already connects to your GitHub account over SSH, skip to the connection check below.

## Step 1 — Make an SSH key

An SSH key is how GitHub knows it is really you, without typing a password every time.

```bash
ssh-keygen -t ed25519 -C "your.email@example.com"
```

Accept the default file location if you do not already have a key there. **If it asks to overwrite an existing key, stop and ask your mentor.** Choose a passphrase to protect your key, then enter it again to confirm.

## Step 2 — Copy the key

```bash
cat ~/.ssh/id_ed25519.pub
```

It prints one long line starting with `ssh-ed25519`. **Select and copy the whole line**, including
the email at the end.

## Step 3 — Give the key to GitHub

1. Go to <https://github.com/settings/keys>
2. Click **New SSH key**
3. **Title:** anything — "my laptop" is fine
4. **Key:** paste what you copied
5. Click **Add SSH key**

## Step 4 — Check it worked

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

Next: [clone your team repository](git.md#clone-your-team-repository).

[Hackathon overview](README.md) · [Git setup and workflow](git.md) · [SSH setup](ssh.md) · [Redeem your OpenAI code](openai-redemption.md)

