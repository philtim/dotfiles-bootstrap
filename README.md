# dotfiles-bootstrap

One-file public bootstrap for [philtim/dotfiles](https://github.com/philtim/dotfiles) (private). Paste this into Terminal on a fresh Mac:

```bash
curl -fsSL https://raw.githubusercontent.com/philtim/dotfiles-bootstrap/main/bootstrap | bash
```

The `bootstrap` script:

1. Verifies macOS.
2. Installs the Xcode CLI tools and waits for the GUI dialog.
3. Installs Homebrew (Apple Silicon / Intel auto-detected).
4. Installs `gh` and runs `gh auth login --web` so you sign in via your browser — no PATs in the URL.
5. `gh repo clone philtim/dotfiles ~/.dotfiles` (uses the gh credentials, works for private repos).
6. `exec ~/.dotfiles/setup.sh`.

Everything else — Homebrew bundle, macOS defaults, stow, plugin installs, BTT restore, post-install walkthrough — happens inside the private dotfiles repo. This is intentionally a tiny separate public surface so the main dotfiles repo can stay private without losing the one-liner setup story.

If you've forked the dotfiles repo, change `REPO="philtim/dotfiles"` at the top of `bootstrap` to your own path.
