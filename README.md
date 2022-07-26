# Dev-env Setup

[![Conventional Commits](https://img.shields.io/badge/Conventional%20Commits-1.0.0-%23FE5196?logo=conventionalcommits&logoColor=white)](https://conventionalcommits.org)
[![Issues](https://img.shields.io/github/issues/xu-minghao317/dotfiles-macOS)](https://github.com/xu-minghao317/dotfiles-macOS/issues)

## Workflow

1. Upgrade macOS.
2. Install `Command Line Tools`.

   ```shell
   xcode-select --install
   ```

3. Run `dotbot`.  
   _Remove `Xcode` and `mactex-no-gui` from `Brewfile` if in hurry._

   ```shell
   git clone https://github.com/xu-minghao317/dotfiles.git ~/.dotfiles --recursive --depth=1
   cd ~/.dotfiles && ./install
   ```

4. Install [Fira Code Nerd Font](https://www.nerdfonts.com/font-downloads) for iTerm2.

5. Migrate `GPG` and `SSH` keys safely.

## Optional

1. Remove all `.DS_Store` files and set a default Finder view option by pressing <kbd>CMD</kbd>.

   ```shell
   kill finder
   find . -name ".DS_Store" -type f -delete
   ```

2. Turn on Touch ID for `sudo`.

   ```shell
   sudo chmod +w /etc/pam.d/sudo
   sudo nvim /etc/pam.d/sudo
   ```

   Change it to ↓

   ```shell
   # sudo: auth account password session
   auth       sufficient     pam_tid.so
   auth       sufficient     pam_smartcard.so
   auth       required       pam_opendirectory.so
   account    required       pam_permit.so
   password   required       pam_deny.so
   session    required       pam_permit.so
   ```

   Then restore permissions

   ```shell
   sudo chmod -w /etc/pam.d/sudo
   ```
