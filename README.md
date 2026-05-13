# Oh My Posh - Paladin173 Theme

Custom Oh My Posh theme for PowerShell and WSL/Linux.

Theme includes:

* Multi-line prompt
* Shell indicator
* Time/date
* CPU/RAM usage
* Execution timing
* Clean path display
* Powerline separators
* Nerd Font support

---

# Requirements

Install:

* PowerShell 7+
* Oh My Posh
* Nerd Font
* Windows Terminal (recommended)

Recommended font:

* CaskaydiaCove Nerd Font
* MesloLGM Nerd Font

---

# Windows PowerShell Setup

Run this entire block in PowerShell:

```powershell
winget install JanDeDobbeleer.OhMyPosh --source winget

oh-my-posh font install CascadiaCode

New-Item -ItemType Directory -Force "$HOME\.poshthemes" | Out-Null

Invoke-WebRequest `
  -Uri "https://raw.githubusercontent.com/Paladin173/ohmyposh-paladin173/main/paladin173.json" `
  -OutFile "$HOME\.poshthemes\paladin173.json"

New-Item -Path $PROFILE -ItemType File -Force

@'
oh-my-posh init pwsh --config "$HOME\.poshthemes\paladin173.json" | Invoke-Expression
'@ | Set-Content $PROFILE

Write-Host ""
Write-Host "Theme installed successfully."
Write-Host "Set Windows Terminal font to:"
Write-Host "CaskaydiaCove Nerd Font"
```

Then:

1. Restart Windows Terminal
2. Set font to:
   `CaskaydiaCove Nerd Font`

---

# WSL / Ubuntu Setup

Run this entire block in WSL Ubuntu:

```bash
sudo apt update && sudo apt install unzip curl -y

curl -s https://ohmyposh.dev/install.sh | bash -s

mkdir -p ~/.poshthemes

curl -o ~/.poshthemes/paladin173.json \
https://raw.githubusercontent.com/Paladin173/ohmyposh-paladin173/main/paladin173.json

echo 'export PATH=$PATH:~/.local/bin' >> ~/.bashrc

echo 'eval "$(oh-my-posh init bash --config ~/.poshthemes/paladin173.json)"' >> ~/.bashrc

exec bash
```

Then:

1. Open Windows Terminal settings
2. Select your Ubuntu/WSL profile
3. Set font to:
   `CaskaydiaCove Nerd Font`

---

# Repository

```text
https://github.com/Paladin173/ohmyposh-paladin173
```

---

# Preview

```text
   10:07:46 PM | Tuesday    CPU: 89% | RAM: 27/31GB   171ms 
╭─  pwsh   D:  Projects 
╰─
```
