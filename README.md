# dotfiles-bootstrap

One-file public bootstrap for [philtim/dotfiles](https://github.com/philtim/dotfiles) (private). Paste this into a terminal on a fresh Mac **or** a fresh Omarchy (Arch + Hyprland) install:

```bash
curl -fsSL https://raw.githubusercontent.com/philtim/dotfiles-bootstrap/main/bootstrap | bash
```

The `bootstrap` script:

1. Detects the OS (Darwin, or Arch-based Linux).
2. macOS: installs the Xcode CLI tools (waits for the GUI dialog), Homebrew (Apple Silicon / Intel auto-detected), and `gh`.
   Omarchy: installs `git` + `github-cli` via pacman.
3. Runs `gh auth login --web` so you sign in via your browser — no PATs in the URL.
4. `gh repo clone philtim/dotfiles ~/.dotfiles` (uses the gh credentials, works for private repos). If `~/.dotfiles` already exists on `main`, it fast-forwards instead; any other branch is left untouched.
5. Initializes git submodules (tpm etc.).
6. `exec ~/.dotfiles/setup.sh`, which dispatches to the right OS installer.

Everything else — Homebrew bundle / pacman + AUR packages, macOS defaults, stow, plugin installs, post-install walkthrough — happens inside the private dotfiles repo. This is intentionally a tiny separate public surface so the main dotfiles repo can stay private without losing the one-liner setup story.

This file mirrors `install/bootstrap.template` in the private dotfiles repo — change it there and copy it here.

If you've forked the dotfiles repo, change `REPO="philtim/dotfiles"` at the top of `bootstrap` to your own path.
